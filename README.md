# Spam-Lord

Here's our chance to be a SpamLord! Yes, we too can build regexes (regular expressions) to help
spread evil throughout the galaxy!
More specifically, our goal in this assignment is to write regular expressions that extract phone
numbers and regular expressions that extract email addresses.

## Objectives

To start with a trivial example, given
```
jurafsky@stanford.edu
```
our job is to return
```
jurafsky@stanford.edu
```

But we also need to deal with more complex examples created by people trying to shield their
addresses, such as the following types of examples that I'm sure we've all seen:
```
jurafsky(at)cs.stanford.edu
jurafsky at csli dot stanford dot edu
```
we should even handle examples that look like the following (as it appears on our screen; we've used
metachars on this page to make it display properly):
```
<script type="text/javascript">obfuscate('stanford.edu','jurafsky')</script>
```
For all of the above we should return the corresponding email address
`jurafsky@stanford.edu` OR `jurafsky@cs.stanford.edu` OR `jurafsky@csli.stanford.edu`
as appropriate.

Similarly, for phone numbers, we need to handle examples like the following:
```
Mohamed Aly – CMP462 NLP
HW #1
1/4TEL +1-650-723-0293
Phone:
(650) 723-0293
Tel (+1): 650-723-0293
<a href="contact.html">TEL</a> +1&thinsp;650&thinsp;723&thinsp;0293
```
All of which should return the following canonical form:

```
650-723-0293
```

## Regular Expressions
This module provides regular expression matching operations similar to those found in Perl. Both patterns and strings to be searched can be Unicode strings as well as 8-bit strings.

Regular expressions use the backslash character ('\') to indicate special forms or to allow special characters to be used without invoking their special meaning. This collides with Python’s usage of the same character for the same purpose in string literals; for example, to match a literal backslash, one might have to write '\\\\' as the pattern string, because the regular expression must be \\, and each backslash must be expressed as \\ inside a regular Python string literal.

The solution is to use Python’s raw string notation for regular expression patterns; backslashes are not handled in any special way in a string literal prefixed with 'r'. So r"\n" is a two-character string containing '\' and 'n', while "\n" is a one-character string containing a newline. Usually patterns will be expressed in Python code using this raw string notation.

It is important to note that most regular expression operations are available as module-level functions and RegexObject methods. The functions are shortcuts that don’t require we to compile a regex object first, but miss some fine-tuning parameters.

## Observations
We write regular expressions to extract information from the files, for this purpose,
we create a lost of reg-exes which fish out the information from a huge pool of data.

* The regular expressions used for emails are:-

```
'(\w+)@(\w+)\.edu', 
'(\w+)@(\w+)\.(\w+)\.edu',
'(\w+)\.(\w+)@(\w+)\.(\w+)\.edu', 
'(\w+)\.(\w+)@(\w+)\.edu',
'(\w+)(\s)@(\s)(\w+)\.edu',
'(\w+)@(\w+)\.(\w+)\.EDU'
'( (\w+((\.| *do*t)+ *\w+)*(( *∗@*@∗@ )| +∗at*at∗at +)\w+((\.|;| *do*t)+ ?\w+)+) *)', '(\w+(\w+((\.| do*t)+ *\w+)) \(followed by *\"?(( *\(*@\) )| +∗at*at∗at +)\w+((\.|;| *do*t)+ ?\w+)+)'
```
These reg-exes are stored in a list and are iterated through for the whole lot of documents, and the results are overwhelming.

* The regular expressions used for phone numbers are:-
```
'\d\d\d-\d\d\d-\d\d\d\d'
'( (\w+((\.| *do*t)+ *\w+)*(( *∗@*@∗@ )| +∗at*at∗at +)\w+((\.|;| *do*t)+ ?\w+)+) *)'
```
These reg-exes are stored in a list and are iterated through for the whole lot of documents, and the results are overwhelming.


## Results

On running the code, a great deal of precision is reached, but also false positives rise too. Multiple detections can be avoided and the code has room for improvement

The results are,
```
True Positives (82): 
{('ashishg', 'p', '650-723-1614'),
 ('ashishg', 'p', '650-723-4173'),
 ('ashishg', 'p', '650-814-1478'),
 ('bgirod', 'p', '650-723-4539'),
 ('bgirod', 'p', '650-724-3648'),
 ('bgirod', 'p', '650-724-6354'),
 ('dabo', 'p', '650-725-3897'),
 ('dabo', 'p', '650-725-4671'),
 ('dlwh', 'e', 'dlwh@stanford.edu'),
 ('engler', 'e', 'engler@stanford.edu'),
 ('hager', 'e', 'hager@cs.jhu.edu'),
 ('hager', 'p', '410-516-5521'),
 ('hager', 'p', '410-516-5553'),
 ('hanrahan', 'p', '650-723-0033'),
 ('hanrahan', 'p', '650-723-8530'),
 ('horowitz', 'p', '650-725-3707'),
 ('horowitz', 'p', '650-725-6949'),
 ('jks', 'e', 'jks@robotics.stanford.edu'),
 ('jurafsky', 'e', 'jurafsky@stanford.edu'),
 ('jurafsky', 'p', '650-723-5666'),
 ('kosecka', 'p', '703-993-1710'),
 ('kosecka', 'p', '703-993-1876'),
 ('kunle', 'p', '650-723-1430'),
 ('kunle', 'p', '650-725-3713'),
 ('kunle', 'p', '650-725-6949'),
 ('lam', 'e', 'lam@cs.stanford.edu'),
 ('lam', 'p', '650-725-3714'),
 ('lam', 'p', '650-725-6949'),
 ('latombe', 'p', '650-721-6625'),
 ('latombe', 'p', '650-723-0350'),
 ('latombe', 'p', '650-723-4137'),
 ('latombe', 'p', '650-725-1449'),
 ('levoy', 'e', 'ada@graphics.stanford.edu'),
 ('levoy', 'e', 'melissa@graphics.stanford.edu'),
 ('levoy', 'p', '650-723-0033'),
 ('ashishg', 'e', 'ashishg@stanford.edu'),
 ('ashishg', 'e', 'rozm@stanford.edu'),
 ('balaji', 'e', 'balaji@stanford.edu'),
 ('cheriton', 'e', 'cheriton@cs.stanford.edu'),
 ('cheriton', 'e', 'uma@cs.stanford.edu'),
 ('cheriton', 'p', '650-723-1131'),
 ('cheriton', 'p', '650-725-3726'),
 ('dabo', 'e', 'dabo@cs.stanford.edu'),
 ('engler', 'e', 'engler@lcs.mit.edu'),
 ('eroberts', 'e', 'eroberts@cs.stanford.edu'),
 ('eroberts', 'p', '650-723-3642'),
 ('eroberts', 'p', '650-723-6092'),
 ('fedkiw', 'e', 'fedkiw@cs.stanford.edu'),
 ('hager', 'p', '410-516-8000'),
 ('hanrahan', 'e', 'hanrahan@cs.stanford.edu'),
 ('kosecka', 'e', 'kosecka@cs.gmu.edu'),
 ('kunle', 'e', 'darlene@csl.stanford.edu'),
 ('kunle', 'e', 'kunle@ogun.stanford.edu'),
 ('latombe', 'e', 'asandra@cs.stanford.edu'),
 ('latombe', 'e', 'latombe@cs.stanford.edu'),
 ('latombe', 'e', 'liliana@cs.stanford.edu'),
 ('manning', 'e', 'dbarros@cs.stanford.edu'),
 ('manning', 'e', 'manning@cs.stanford.edu'),
 ('nass', 'e', 'nass@stanford.edu'),
 ('nick', 'e', 'nick.parlante@cs.stanford.edu'),
 ('psyoung', 'e', 'patrick.young@stanford.edu'),
 ('rajeev', 'p', '650-723-4377'),
 ('rajeev', 'p', '650-723-6045'),
 ('rajeev', 'p', '650-725-4671'),
 ('rinard', 'e', 'rinard@lcs.mit.edu'),
 ('shoham', 'e', 'shoham@stanford.edu'),
 ('subh', 'p', '650-724-1915'),
 ('subh', 'p', '650-725-3726'),
 ('subh', 'p', '650-725-6949'),
 ('thm', 'e', 'pkrokel@stanford.edu'),
 ('ullman', 'p', '650-494-8016'),
 ('ullman', 'p', '650-725-2588'),
 ('ullman', 'p', '650-725-4802'),
 ('widom', 'e', 'siroker@cs.stanford.edu'),
 ('widom', 'e', 'widom@cs.stanford.edu'),
 ('widom', 'p', '650-723-0872'),
 ('widom', 'p', '650-723-7690'),
 ('widom', 'p', '650-725-2588'),
 ('zelenski', 'e', 'zelenski@cs.stanford.edu'),
 ('zelenski', 'p', '650-723-6092'),
 ('zelenski', 'p', '650-725-8596'),
 ('zm', 'e', 'manna@cs.stanford.edu')}
False Positives (2): 
{('nick', 'e', 'parlante@cs.stanford.edu'),
 ('psyoung', 'e', 'young@stanford.edu')}
False Negatives (35): 
{('levoy', 'p', '650-724-6865'),
 ('levoy', 'p', '650-725-3724'),
 ('levoy', 'p', '650-725-4089'),
 ('manning', 'p', '650-723-7683'),
 ('manning', 'p', '650-725-1449'),
 ('manning', 'p', '650-725-3358'),
 ('nass', 'p', '650-723-5499'),
 ('nass', 'p', '650-725-2472'),
 ('nick', 'p', '650-725-4727'),
 ('ok', 'p', '650-723-9753'),
 ('ok', 'p', '650-725-1449'),
 ('ouster', 'e', 'ouster@cs.stanford.edu'),
 ('ouster', 'e', 'teresa.lynn@stanford.edu'),
 ('pal', 'e', 'pal@cs.stanford.edu'),
 ('pal', 'p', '650-725-9046'),
 ('rinard', 'p', '617-253-1221'),
 ('rinard', 'p', '617-258-6922'),
 ('serafim', 'e', 'serafim@cs.stanford.edu'),
 ('serafim', 'p', '650-723-3334'),
 ('serafim', 'p', '650-725-1449'),
 ('shoham', 'p', '650-723-3432'),
 ('shoham', 'p', '650-725-1449'),
 ('subh', 'e', 'subh@stanford.edu'),
 ('subh', 'e', 'uma@cs.stanford.edu'),
 ('thm', 'p', '650-725-3383'),
 ('thm', 'p', '650-725-3636'),
 ('thm', 'p', '650-725-3938'),
 ('tim', 'p', '650-724-9147'),
 ('tim', 'p', '650-725-2340'),
 ('tim', 'p', '650-725-4671'),
 ('ullman', 'e', 'support@gradiance.com'),
 ('ullman', 'e', 'ullman@cs.stanford.edu'),
 ('vladlen', 'e', 'vladlen@stanford.edu'),
 ('zm', 'p', '650-723-4364'),
 ('zm', 'p', '650-725-4671')}
Summary: tp=82, fp=2, fn=35


```

As, we can see the code needs improvement and hence can be written as **WIP** = **W**ork **I**n **P**rogress
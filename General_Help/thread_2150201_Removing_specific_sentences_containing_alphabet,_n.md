---
title: "Removing specific sentences containing alphabet, numbers and symbols"
date: 2013-05-31
forum: General Help
---

### Post by drofart on 2013-05-31
Hello folks,
   Not sure if it's the right place to ask this question, but it still relates to ubuntu. I have heard about ```
sed
``` and it's capabilities few days back, then i tried to learn it for home use but haha it's a giant to tackle with, ```
REGEX
``` is another story. 

Coming to point, i have some text files that have to edited and i think ```
sed
``` is the preferable tool.

I want to remove all sentences in a file that read like ```
See 19.
``` or ```
See 20 and 31.
``` or ```
See 45, 11.
``` .

Note: Digits are not static and subject to change from 1-99.

Thanks.

---

### Post by drofart on 2013-05-31
Any Idea guyssss...........

---

### Post by Mark Phelps on 2013-05-31
Show a little patience!  Forums rules are to bump no more often than once every 24 hours.

---

### Post by steeldriver on 2013-05-31
something like

```
echo "See 20 and 31. Something. See 45, 11. Something else. See 19. Whatever." | sed -re 's/See[[:space:]]+[0-9]+(([[:space:][:punct:]]|[[:space:]]+and[[:space:]]+)+[0-9]+)?\.[[:space:]]+?//g'
Something. Something else. Whatever.

```

maybe? although for clarity I'd probably split it into 3 separate substitutions using -e expression1 - e expression2 -e expression3

---

### Post by HiImTye on 2013-05-31
```
sed -ie 's|[sS]ee [0-9][^a-zA-Z]*\.||' /path/to/file
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by drofart on 2013-06-01
> **HiImTye said:**
> ```
sed -ie 's|[sS]ee [0-9][^a-zA-Z]*\.||' /path/to/file
```


Thanks for the help it is working well except the following one

```
See 12 and 32
```

Numbers are changeable.

I guess the "and" word is making problems.

---

### Post by drofart on 2013-06-01
> **steeldriver said:**
> something like

```
echo "See 20 and 31. Something. See 45, 11. Something else. See 19. Whatever." | sed -re 's/See[[:space:]]+[0-9]+(([[:space:][:punct:]]|[[:space:]]+and[[:space:]]+)+[0-9]+)?\.[[:space:]]+?//g'
Something. Something else. Whatever.

```

maybe? although for clarity I'd probably split it into 3 separate substitutions using -e expression1 - e expression2 -e expression3

I have used the 2nd part only and It's working like a charm!! Thanks. Should i use the "echo" as there are no fix numbers on any file?

If you don't mind i will ask for a bit more favor :) What if it will be a bit longer like say "See 32, 41, 88, 39."

---

### Post by drofart on 2013-06-01
> **Mark Phelps said:**
> Show a little patience!  Forums rules are to bump no more often than once every 24 hours.

Sorry for that but believe me, Ubuntuforums is a place where i get quickest replies :)

Love to be in ubuntu family :guitar:

---

### Post by steeldriver on 2013-06-01
> **drofart said:**
> I have used the 2nd part only and It's working like a charm!! Thanks. Should i use the "echo" as there are no fix numbers on any file?

If you don't mind i will ask for a bit more favor :) What if it will be a bit longer like say "See 32, 41, 88, 39."

The "echo" part was only to test it - you would use it like

```
sed -re 's/See[[:space:]]+[0-9]+(([[:space:][:punct:]]|[[:space:]]+and[[:space:]]+)+[0-9]+)?\.[[:space:]]+?//g' ***yourfile***
``` 

or separate out the individual cases to make it easier to understand like

```
sed -r \
    -e 's/See[[:space:]]+[0-9]+\.[[:space:]]+?//g' \ 
    -e 's/See[[:space:]]+[0-9]+[[:space:][:punct:]]+[0-9]+\.[[:space:]]+?//g' \ 
    -e 's/See[[:space:]]+[0-9]+[[:space:]]+and[[:space:]]+[0-9]+\.[[:space:]]+?//g' * yourfile*
``` 

To make it handle the "See 32, 41, 88, 39." case you could modify the 'space number space-or-punct number' pattern to make it read 'space number one-or-more-(space-or-punct number)s'

```
sed -r \
    -e 's/See[[:space:]]+[0-9]+\.[[:space:]]+?//g' \ 
    -e 's/See[[:space:]]+[0-9]+[COLOR=#0000ff]**(**[/COLOR][[:space:][:punct:]]+[0-9]+[COLOR=#0000ff]**)+**[/COLOR]\.[[:space:]]+?//g' \ 
    -e 's/See[[:space:]]+[0-9]+[[:space:]]+and[[:space:]]+[0-9]+\.[[:space:]]+?//g' * yourfile*
``` 

or combine the first 2 like 'space number [COLOR=#0000ff]zero[/COLOR]-or-more-(space-or-punct number)s'

```
sed -r \
    -e 's/See[[:space:]]+[0-9]+[COLOR=#0000ff]**(**[/COLOR][[:space:][:punct:]]+[0-9]+[COLOR=#0000ff]**)***[/COLOR]\.[[:space:]]+?//g' \
    -e 's/See[[:space:]]+[0-9]+[[:space:]]+and[[:space:]]+[0-9]+\.[[:space:]]+?//g' * yourfile*
```

or equivalently (I think)

```
sed -r \
    -e 's/See[[:space:]]+[0-9]+[COLOR=#0000ff]**(**[/COLOR][[:space:][:punct:]]+[0-9]+[COLOR=#0000ff]**)***[/COLOR]\.[[:space:]][COLOR=#0000ff]*****[/COLOR]//g' \
    -e 's/See[[:space:]]+[0-9]+[[:space:]]+and[[:space:]]+[0-9]+\.[[:space:]][COLOR=#0000ff]*****[/COLOR]//g' * yourfile*
```

[I don't know why I used +? for the optional trailing space in the previous post, * would be more usual]

---

### Post by HiImTye on 2013-06-01
> **drofart said:**
> 
Thanks for the help it is working well except the following one

Code:

See 12 and 32

Numbers are changeable.

I guess the "and" word is making problems.


```
sed -ie 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.||g' /path/to/file
```
;)


[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by mikeym on 2013-06-01
If you would like all your matches in a slightly more compact form:

```
sed -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi'
```

This will match

> See 20 and 31. Something. See 45, 11. Something else. See 19. Whatever. see 2,45, 34 and 15. see 1 and 22.

as

> Something. Something else. Whatever.

Note the use of the switch "-r" which uses *sed*'s extended regex which change it's behaviour from having to escape regex characters "()+?{}" with a "\" which make it a bit more readable in my opinion.

---

### Post by drofart on 2013-06-01
> **steeldriver said:**
> The "echo" part was only to test it - you would use it like

```
sed -re 's/See[[:space:]]+[0-9]+(([[:space:][:punct:]]|[[:space:]]+and[[:space:]]+)+[0-9]+)?\.[[:space:]]+?//g' ***yourfile***
``` 

or separate out the individual cases to make it easier to understand like

```
sed -r \
    -e 's/See[[:space:]]+[0-9]+\.[[:space:]]+?//g' \ 
    -e 's/See[[:space:]]+[0-9]+[[:space:][:punct:]]+[0-9]+\.[[:space:]]+?//g' \ 
    -e 's/See[[:space:]]+[0-9]+[[:space:]]+and[[:space:]]+[0-9]+\.[[:space:]]+?//g' * yourfile*
``` 

To make it handle the "See 32, 41, 88, 39." case you could modify the 'space number space-or-punct number' pattern to make it read 'space number one-or-more-(space-or-punct number)s'

```
sed -r \
    -e 's/See[[:space:]]+[0-9]+\.[[:space:]]+?//g' \ 
    -e 's/See[[:space:]]+[0-9]+[COLOR=#0000ff]**(**[/COLOR][[:space:][:punct:]]+[0-9]+[COLOR=#0000ff]**)+**[/COLOR]\.[[:space:]]+?//g' \ 
    -e 's/See[[:space:]]+[0-9]+[[:space:]]+and[[:space:]]+[0-9]+\.[[:space:]]+?//g' * yourfile*
``` 

or combine the first 2 like 'space number [COLOR=#0000ff]zero[/COLOR]-or-more-(space-or-punct number)s'

```
sed -r \
    -e 's/See[[:space:]]+[0-9]+[COLOR=#0000ff]**(**[/COLOR][[:space:][:punct:]]+[0-9]+[COLOR=#0000ff]**)***[/COLOR]\.[[:space:]]+?//g' \
    -e 's/See[[:space:]]+[0-9]+[[:space:]]+and[[:space:]]+[0-9]+\.[[:space:]]+?//g' * yourfile*
```

or equivalently (I think)

```
sed -r \
    -e 's/See[[:space:]]+[0-9]+[COLOR=#0000ff]**(**[/COLOR][[:space:][:punct:]]+[0-9]+[COLOR=#0000ff]**)***[/COLOR]\.[[:space:]][COLOR=#0000ff]*****[/COLOR]//g' \
    -e 's/See[[:space:]]+[0-9]+[[:space:]]+and[[:space:]]+[0-9]+\.[[:space:]][COLOR=#0000ff]*****[/COLOR]//g' * yourfile*
```

[I don't know why I used +? for the optional trailing space in the previous post, * would be more usual]

Working !!!!!!!! :guitar: Thanks a lot.....

> **HiImTye said:**
> ```
sed -ie 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.||g' /path/to/file
```
:wink:



Sorry buddy but not working. Any way thank you very very much for you spent atleast few mins for me. :)

---

### Post by drofart on 2013-06-01
> **mikeym said:**
> If you would like all your matches in a slightly more compact form:

```
sed -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi'
```

This will match



as



Note the use of the switch "-r" which uses *sed*'s extended regex which change it's behaviour from having to escape regex characters "()+?{}" with a "\" which make it a bit more readable in my opinion.

Like the code of @hilmtye, it is also producing a file without any change at all. 
Thanks.

---

### Post by HiImTye on 2013-06-01
> **drofart said:**
> :guitar:Sorry buddy but not working. Any way thank you very very much for you spent atleast few mins for me. :)

really?
```
$ echo some text. See 12, 13, 54, and 7. see 6, 9, 4. see 1 and 2. some more text > out.text
$ sed -ie 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.||g' out.text
$ cat out.text
some text.    some more text

```
works for me 

edit: you do know that -i edits inline, correct? the original file will be changed [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by steeldriver on 2013-06-01
both HilmTye's and mikeym's versions work for me (although one treats trailing space differently - which may be what you want) - are you sure you're using them right?

```
$ sed -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi' yourfile 
Something. Something else. New case. Whatever.
$ 
$ sed -e 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.||g' yourfile 
 Something.  Something else.  New case.  Whatever.

```

As you can see, there's often more than one way to express the pattern match - just choose what makes the best sense / readability to you - try to read them yourself and understand what they're doing so you can modify them if you need to

---

### Post by HiImTye on 2013-06-01
> **steeldriver said:**
> although one treats trailing space differently

you're right, it should be
```
sed -ie 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.[ ]*||g' /path/to/file
``` 

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by drofart on 2013-06-01
> **HiImTye said:**
> really?
```
$ echo some text. See 12, 13, 54, and 7. see 6, 9, 4. see 1 and 2. some more text > out.text
$ sed -ie 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.||g' out.text
$ cat out.text
some text.    some more text

```
works for me 

edit: you do know that -i edits inline, correct? the original file will be changed 

Ya i know about common options, the regex is overwhelming. The error both in yours and @steeldriver's code is that they both are producing 0bytes files when output is mentioned and doing nothing to the file when editing inline. There may be some kind of mistake from my side but all is well when end is well :)

By The Way regex is too complicated for me and it seems i ll forever depend on ubuntuforums for that.

---

### Post by mikeym on 2013-06-01
> **steeldriver said:**
> both HilmTye's and mikeym's versions work for me (although one treats trailing space differently - which may be what you want) - are you sure you're using them right?

```
$ sed -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi' yourfile 
Something. Something else. New case. Whatever.
$ 
$ sed -e 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.||g' yourfile 
 Something.  Something else.  New case.  Whatever.

```

As you can see, there's often more than one way to express the pattern match - just choose what makes the best sense / readability to you - try to read them yourself and understand what they're doing so you can modify them if you need to

Yep. There's more than one way to regex a [Cc]at. :P

I would say that out of these 2, mine is a little stricter about what it will match; it will only match strings that you indicated. There are some odd cases which the other one would match. For example try:

```

echo 'test. see 10-$%£,() and £$&.£$%    . testing.' | sed -e 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.||g'

```

You're probably best looking into how *sed* reads input a bit more. The code I gave was just a call to *sed* to perform the substitution you wanted. It can either be used with a filename appended to the command as **steeldriver** suggested to read the input from a file, or it can read from STDIN (standard input) where it can be piped into *sed* from another command using the pipe operator (in bash "|") or read from input at the terminal. 

So by way of examples: 

```

# my original command reads input from the terminal; just try typing something and pressing enter
sed -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi' 

# reads input from a file and outputs it to STDOUT (standard output; the screen)
sed -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi'  myfilename

# performs substitutions on the file with the "-i" switch so that the input file is modified
sed -i -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi'  myfilename

# takes output from one command (in this case echo) and pipes it into sed which sends it to STDOUT
echo "one two see 4,5, 6 and 71." | sed -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi'

# takes STDOUT from sed and redirects it to a file with ">" 
sed -re 's/see\s+[[:digit:]]+(,\s*[[:digit:]]+)*(\s+and\s+[[:digit:]]+)?\.\s*//gi'  myfilename > outputfilename

```

---

### Post by drofart on 2013-06-01
It seems that the function to edit the first post to mark it as solve is no more available.

---

### Post by drofart on 2013-06-01
> **HiImTye said:**
> you're right, it should be
```
sed -ie 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.[ ]*||g' /path/to/file
``` 



Don't know what is the problem but see the image and you can guess, directly in terminal it isn't even editing inline but producing a mirror file with a "e" append to the file name. weird!

---

### Post by steeldriver on 2013-06-01
It's likely treating -ie to mean edit inline but save a backup with 'e' as the suffix

See man sed:
```
       -i[SUFFIX], --in-place[=SUFFIX]

              edit files in place (makes backup if extension supplied)


```

That's different from 

```
sed [COLOR=#0000ff]**-i -e**[/COLOR] 's|[sS]ee [0-9][^a-zA-Z]*\(and\)*[^a-zA-Z]*\.[ ]*||g'
```

---

### Post by HiImTye on 2013-06-01
odd, it works for me, as shown above, but the man does indeed say that. I'll have to keep that in mind when I finally upgrade to 13.04

---


---
title: "Shell script problem - mod (%) not working in xscreensaver"
date: 2008-02-02
forum: General Help
---

### Post by acl123 on 2008-02-02
Hi I wrote a script that is supposed to output the contents of a file using sed. It starts at a random line number and prints to the end. My script looks like this:

```
TotalLineCount=$(wc -l < $1)
RandomModByTotalCount=$[$RANDOM % $TotalLineCount]
sed -n $[$RandomModByTotalCount],$[$TotalLineCount]p $1
```

OK that works.

Now I want to user that for my screensavers using **xscreensaver**.

So I go to xscreensaver's "Text Manipulation" settings and give it the name of my program with a text file as the argument.

But when I run a screensaver, instead of getting the text from my file I get this error message:
```
/home/myuser/myscript.sh :  3: %: not found
sed: -e expression #1, char 2: unknown command `['

```

So it looks like the mod symbol *%* is not recognized. Why would it not be recognized when run through xscreensaver but it is recognized when I run my command in the terminal?

---

### Post by dcstar on 2008-02-03
> **acl123 said:**
> Hi I wrote a script that is supposed to output the contents of a file using sed. It starts at a random line number and prints to the end. My script looks like this:

```
TotalLineCount=$(wc -l < $1)
RandomModByTotalCount=$[$RANDOM % $TotalLineCount]
sed -n $[$RandomModByTotalCount],$[$TotalLineCount]p $1
```

OK that works.

Now I want to user that for my screensavers using **xscreensaver**.

So I go to xscreensaver's "Text Manipulation" settings and give it the name of my program with a text file as the argument.

But when I run a screensaver, instead of getting the text from my file I get this error message:
```
/home/myuser/myscript.sh :  3: %: not found
sed: -e expression #1, char 2: unknown command `['

```

So it looks like the mod symbol *%* is not recognized. Why would it not be recognized when run through xscreensaver but it is recognized when I run my command in the terminal?

Because your terminal session is run in a shell, and you have not specified that this runs in a shell.

Look at any of the various scripts in your system for examples.

---

### Post by accatagon on 2008-02-03
It's running your program as a perl script. Seriously, try running it with perl: you get the same results.

You need to begin the very first line of your script with "#!/bin/bash", since that is what the shell you were using is. If you do this, then it should execute it as a shell script any time any program runs it. The problem is that, although Bash will automatically run everything using the Bash program (duh), other programs get to pick and choose what they want to run your program with, so you have to explicitly specify what they should use.  For future reference, you should do this with EVERY non-compiled executable. "#!/usr/bin/perl" for perl scripts and "#!/usr/bin/python" for python scripts and so on. Note that the "#" character represents a comment in all the languages. Also note that it has to be at the VERY beginning of the file. That means no spaces or other comments or newlines or anything. Tell me if that helps. 

I hope I have shed some more light on the issue.

---

### Post by acl123 on 2008-02-04
Aaaaaahhhh makes perfect sense! Thanks guys!

---


---
title: "Using &quot;find&quot; to list files with different extentions"
date: 2015-02-08
forum: General Help
---

### Post by ric_Poirier on 2015-02-08
Hi,

I have films in directory
```
~/Films
```
with different file extentions (.avi, .mp4 and .mkv) and I would like to generate a list of all these movies in a file. Here is the general structure of the "Films" directory:
```

**/Films**
**/Films/action/**
/Film/action/movie1.avi
/Film/action/movie2.avi
/Film/action/movie3.mkv
**/Films/drama/**
/Film/drama/movie4.avi
/Film/drama/movie5.mkv
/Film/drama/movie6.mp4
**/Films/sci-fi/**
...

```
The different movies are stored in the "action", "drama", "sci-fi" (and so on) sub-directories. I want my list to be:
```

movie1.avi
movie2.avi
movie3.mkv
movie4.avi
movie5.mkv
movie6.mp4
...

```

To acheive this, I tried this command, which is reported to work in some forums:

```

cd ~/Films
find . -name "*.mp4" -o -name ".avi" -o -name ".mkv" -fprintf films "%f\n"

```

which results in the following list in the "films" file:
```

movie3.mkv
movie5.mkv

```

All other titles don't appear.

What is going on?

---

### Post by steeldriver on 2015-02-08
I think you've run up against the "gotcha" about how the find command logically  combines tests - to get the behaviour you're expecting, you probably need to group the expressions explicitly i.e.

```

find . **\(** -name "*.mp4" -o -name ".avi" -o -name ".mkv" **\)** -fprintf films "%f\n"

```

---

### Post by ric_Poirier on 2015-02-08
Thank you, it works (with "*.avi" and "*.mkv" of course, my bad)!

I had came across this in the find manpages but did not think it matter in my case:

```

 OPERATORS
       Listed in order of decreasing precedence:

       ( expr )
              Force precedence.  Since parentheses are special to the shell, you will normally need to quote them.  Many of the examples  in  this  manual  page  use  backslashes  for  this  purpose:
              `\(...\)' instead of `(...)'.

```

Still, I don't understand why we need this. Force precedence? What does it do that was not done with the previous command?

Thanks

---

### Post by papibe on 2015-02-08
Hi ric_Poirier.

All 'find' options return a logic value (true or false), and by default are 'and' together.

To improve performance, 'find' will not evaluate redundant expressions. For instance, if you have
```
expresion1 and expression2
```
If 'find' determines that expression1 is false, 'find' will skip evaluating expression2 because 'false and whatever' is always false.

Another example:
```
$ ls
not_this_file.txt  this_file.txt

$ find -name '*file*' -name '*not*'
./not_this_file.txt

$ find -name '*file*' -o -name '*not*'
./this_file.txt
./not_this_file.txt

```
Note that by defualt 'find' would print the results, but if you explicitly ask for print, you are effectively adding another logical switch:
```
$ find -name '*file*' -o -name '*not*'
./this_file.txt
./not_this_file.txt

$ find -name '*file*' -o -name '*not*' -print
$

```
And that makes the case for parenthesis:
```
$ find \( -name '*file*' -o -name '*not*' \) -print
./this_file.txt
./not_this_file.txt

```
Does that help? Let us know if you have more questions.
Regards.

---

### Post by Holger_Gehrke on 2015-02-08
The '-o' and '-or' have a lower precedence than '-a', '-and' and **the implied 'and'** between two option which don't have anything between them. So the -name '*.mkv'  and the '-fprint' are connected by an implied 'and' while the others aren't. By putting parentheses around all the name options they are all getting processed before the -print is.

---

### Post by ric_Poirier on 2015-02-08
Hi guys, thanks for taking time to answer,

So from your answers, I understand that my command:

```

find . -name "*.mp4" -o -name "*.avi" -o -name "*.mkv" -fprintf films "%f\n

```

has to be tought of as:

```

find . -name ".*mp4" **OR** -name "*.avi" **OR** -name "*.mkv" **AND (IMPLIED)** -print

```

and thus the computer evaluated

```

-name "*.mkv" -fprintf films "%f\n

```

first (hence my mkv-limited output) because AND (even implied) has a higher precedence than OR. So the parentheses rise the precedence of the OR-chain so as to evaluate all of it before printing it.

Is that right?

---

### Post by papibe on 2015-02-08
You got it.

You can see it in this simple example too: since all my files have the part 'file' the first part of the expression will be TRUE. Since 'true OR whatever' is always true, 'find' won't execute the second part of the expression. Unfortunately the -print is in the second part.
```
$ ls
not_this_file.txt  this_file.txt

$ find -name '*file*' -o  -name '*not*' -print
$

$ find -name '*file*' -o \( -name '*not*' -print \)
$

```
Now if you change the order, for one file the first expression would be false, then just allowing the second part of the expression to be executed (because 'FALSE or whatever' can't be shortcut):
```
$ find -name '*not*' -o -name '*file*' -print
./this_file.txt
```
Hope it helps.
Regards.

---

### Post by ric_Poirier on 2015-02-08
I understand, thank you!!

---


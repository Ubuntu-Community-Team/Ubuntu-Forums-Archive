---
title: "[SOLVED] How do I output &amp;quot;ls&amp;quot; to gedit, without creating a file"
date: 2007-09-15
forum: General Help
---

### Post by Jose Catre-Vandis on 2007-09-15
Want to output the result of an "ls" command on a directory straight into gedit, so that I can edit it further in gedit before saving or copy and pasting to web etc.

I have tried all sorts of combinations of pipes and redirects to make this work, but I must be missing a golden rule :)

My logic tells me this should work:
```
ls | gedit
```
but "computer says no", and I can see it is somewhat simplistic.

---

### Post by Jose Catre-Vandis on 2007-09-16
Got closer:
```
ls > mypdfs && gedit mypdfs && rm mypdfs &
```

This outputs ls to a file, opens the file in gedit, and then deletes the file if I close gedit wihtout saving. Not pretty!

---

### Post by bogolisk on 2007-09-16
> **Jose Catre-Vandis said:**
> Got closer:
```
ls > mypdfs && gedit mypdfs && rm mypdfs &
```

This outputs ls to a file, opens the file in gedit, and then deletes the file if I close gedit wihtout saving. Not pretty!

I'm not sure you can do what you want in bash. In zsh, it's pretty simple:
```

gedit =(ls)

```

---

### Post by nick_h on 2007-09-16
You can do it with vi:
```
ls | vi -
```
but I don't think gedit has an option to edit stdin.

---

### Post by Jose Catre-Vandis on 2007-09-16
Thanks, tried both and no joy :(

---

### Post by bogolisk on 2007-09-16
> **Jose Catre-Vandis said:**
> Thanks, tried both and no joy :(

To use ```
gedit =(ls)
``` You'll have to run zsh as shell, not the default bash.

---

### Post by DirtDawg on 2007-09-16
Just for the record, "ls | vi -" worked fine for me. Well, I used "ls | gvim -".

---

### Post by Jose Catre-Vandis on 2007-09-22
Seems that "ls | gedit" used to work up to a couple of years ago but now is an unresolved bug

[https://bugs.launchpad.net/gedit/+bug/9054](https://bugs.launchpad.net/gedit/+bug/9054)

---

### Post by nick_h on 2007-09-22
From that bug it doesn't look like anyone is in any hurry to fix it.  It is a bug in Dapper, Edgy, Fesity and is still in Gutsy.

---

### Post by Dji on 2008-06-30
I've tried this  > gedit `ls` and it's strange, it opens as many empty files as I have files, and these opened files have strange names such as ... :s
Something wrong in my command ? :confused:

---

### Post by geirha on 2008-06-30
```
ls | xargs gedit
```

Though I don't understand why you need to use ls, why not just ```
gedit *
``` ?

---

### Post by Dji on 2008-06-30
Thank geirha for your reply.
But
```
ls | xargs gedit
```
gives the same trouble as
```
ls | gedit `ls`
```
to me.
I got that (very strange names) :
[[IMG]http://img164.imageshack.us/img164/3232/tmptw6.th.png[/IMG]](http://img164.imageshack.us/my.php?image=tmptw6.png)

And if I don't simply use ```
gedit *
``` It's because in fact I don't want to open evevry files but some specefic ones. (I ve used the example  ```
 gedit `ls` 
``` to simply things :)
But in fact I would like to be able to open a list of files resulting of a linux comand such as grep or sed and so on :)

---

### Post by mkrahmeh on 2008-06-30
first redirect the output to a file then open that file using gedit (u need to pass the file name as an argument to gedit)

```
ls > *file_name* | gedit *file_name*
```

it worked fine with me

---

### Post by geirha on 2008-07-01
> **Dji said:**
> Thank geirha for your reply.
But
```
ls | xargs gedit
```
gives the same trouble as
```
ls | gedit `ls`
```
to me.
I got that (very strange names) :
[[IMG]http://img164.imageshack.us/img164/3232/tmptw6.th.png[/IMG]](http://img164.imageshack.us/my.php?image=tmptw6.png)

And if I don't simply use ```
gedit *
``` It's because in fact I don't want to open evevry files but some specefic ones. (I ve used the example  ```
 gedit `ls` 
``` to simply things :)
But in fact I would like to be able to open a list of files resulting of a linux comand such as grep or sed and so on :)

Those filenames are very strange indeed, I'm unable to reproduce that myself. Can you give me an example filename that gives this result when you do gedit filename ?

Also, instead of greping and seding the output of ls, you might be able to do the same with find.

---

### Post by Dji on 2008-07-01
Hi Mkrahmeh
```
ls > file_name | gedit file_name
```
Thank you Mkrahmeh but that creats a file holding all files' name and then it opens that file. so at the end I have only one file x)
----------------------------------------------------------------------
Hi Geirha
> Those filenames are very strange indeed, I'm unable to reproduce that myself. Can you give me an example filename that gives this result when you do gedit filename ?

Also, instead of greping and seding the output of ls, you might be able to do the same with find.
I'm in a folder holding 2 files named iron.srt and tmp.txt
then by doing ```
ls | xargs gedit
``` or ```
gedit `ls`
```
I get 3 files opened (and not 2 lol) named : 
[00m[00miron.srt[00m
[00mtmp.txt[00m
[m

So strange names that I think it could interest Scully and Mulder :)
But I tried with the find command ```
gedit `find *`
``` or if I want to open only .txt files ```
 gedit `find *|grep .txt`
```
And That WORKS  fine ^__^
Thank you very much for the advise geirha :D !!

I still don't understand why it doesn't work with the ls command XD lol

---

### Post by FranMichaels on 2008-07-01
```
gedit *.txt
```
You don't need to use find or anything.

or all text files that begin with the letter a

a*.txt

For example if you wanted to move all the files with *.txt
mv *.txt ~/somefolder/

It's globbing :)

You can also get fancy with regular expressions
[http://en.wikipedia.org/wiki/Regular_expression#POSIX_character_classes](http://en.wikipedia.org/wiki/Regular_expression#POSIX_character_classes)

EDIT: One more thing you said gedit `ls` didn't work for you. Does it work if you use gedit `"ls"`

---

### Post by unutbu on 2008-07-01
The funny characters are terminal control characters. In your case, they are probably used to define the color of the text. You could try to get rid of the color by running

```
ls --color=none | xargs gedit
```

Nevertheless, I don't recommend this. `ls` is the wrong tool to use when you want to pipe the name of files to another process. find is much better because it can handle filesnames with spaces. ls can't.


```

find . -maxdepth 1 -type f -name "*.txt" -print0 | xargs -0 gedit

-maxdepth 1   only list files in the top level directory, not subdirectories

-type f       only list files, not directories
-name "*.txt" only list files with extension .txt
-print0       print a null character at the end of the file. This allows the name of the file to contain a space.

xargs -0 tells xargs to expect a stream of filenames separated by null characters.

```

---

### Post by geirha on 2008-07-01
> **Dji said:**
> I'm in a folder holding 2 files named iron.srt and tmp.txt
then by doing ```
ls | xargs gedit
``` or ```
gedit `ls`
```
I get 3 files opened (and not 2 lol) named : 
[00m[00miron.srt[00m
[00mtmp.txt[00m
[m

So strange names that I think it could interest Scully and Mulder :)
But I tried with the find command ```
gedit `find *`
``` or if I want to open only .txt files ```
 gedit `find *|grep .txt`
```
And That WORKS  fine ^__^
Thank you very much for the advise geirha :D !!

I still don't understand why it doesn't work with the ls command XD lol

I think those strange names are due to color-codes. Do you happen to have an alias that says ls='ls --color=always' or something? If so, change it from always to auto. find does not produce colored output, so that might be why find works better than ls. 

In this particular case though, you could've just done 
```
gedit *.txt
```
or if you need to do recursive search for all txt-files:
```
find . -name "*.txt" -print0 | xargs -0 gedit
```

---

### Post by Dji on 2008-07-02
OMG lol ^__^ I've complelty forgotten that I've made an alias with my ls command in my .bashrc. And you were right evryone it was cause there was the color option. Me --> brainless x)
Thank you very much everyone for all your advices ^^ now everything works well :)

---

### Post by Jose Catre-Vandis on 2008-07-02
> **mkrahmeh said:**
> first redirect the output to a file then open that file using gedit (u need to pass the file name as an argument to gedit)

```
ls > *file_name* | gedit *file_name*
```

it worked fine with me

This solves it for me, many thanks mkrahmeh :D

---


---
title: "rename command"
date: 2007-06-18
forum: General Help
---

### Post by oldcpu on 2007-06-18
In another distribution, the rename command is used like this:
```
rename oldname newname *.foo
```
In Ubuntu however, I have to do this:
```
rename s/oldname/newname/ *.foo
```
Is there a way I can use the first code in Ubuntu?

The first code is superior to the second because I can use tab-completion with it.

---

### Post by dannyboy79 on 2007-06-19
the mv command can be used to rename stuff as well. it's as easy as 
mv text.txt text1.txt
and tab completion would work. As far as the rename command in Ubuntu, you can read the man pages, man rename. I can't be more help because I don't use rename ever, I use mv.

---

### Post by oldcpu on 2007-06-20
> the mv command can be used to rename stuff as well.
Of course.  But what is the point if it can not rename multiple files?

> As far as the rename command in Ubuntu, you can read the man pages, man rename.
Did...  But this rename command is behaving differently as mentioned in the original post.

> I can't be more help because I don't use rename ever, I use mv.
So basically, you just posted to tell me to read the manual?

---

### Post by Mr. C. on 2007-06-20
The rename command to which you are referring is a little perl script, which uses regular expressions to perform bulk renames.  It is more powerful that the simple old rename you are used to.

You can modify the script (locate rename) and place it in your own bin directory, or use a shell function :

```
function myrename {
   old="$1"; new="$2"; shift; shift; 
   echo rename s/$old/$new/ "$@"
}
```

I've left an echo in there so you can see how it works - remove the echo word to run it.

You can also use bash command and parameter completion to perform the magic for you, transforming

 rename old new filelist

into

  rename s/old/new/ filelist

with a keybinding.

MrC

---

### Post by atria on 2007-06-20
If you want to rename many files at once, check out this package: renameutils

---

### Post by oldcpu on 2007-06-20
Thanks, Mr. C.

Is that code only a temporary one?  As in it is saved in RAM?

I am glad that there is a way I can get the tab-completion back.  But how would I put the above code in script form?  I tried coping it into both bash and perl (I am not a programmer in either), but failed.

---

### Post by dannyboy79 on 2007-06-20
> **oldcpu said:**
> So basically, you just posted to tell me to read the manual?
You can answer your own smart __s question by reading my entire post and not just the last 2 lines. If you missed it than I'll explain it again for you, you can rename a file using the mv command which will get you your tab completion back.

If you wanted to know how to rename multiple files than maybe it'd be a good idea to say that next time.

---

### Post by Mr. C. on 2007-06-20
Oldpc,

The function I posted is temporary if you enter it into your current shell and use it.  If you want to be able to use it now and in subsequent shells, you can place it in your .bashrc file.  Edit your ~/.bashrc file, and copy/past the code. On subsequent bash shells, the function will be available.

I just copied/pasted the code again too (to ensure I didn't have a typo).  It works just fine.  If you find an error, please show the actual  output on your screen, rather than interpret it and report "it fails".  Exact error messages and output is crucial to getting you the help you desire.

MrC

---

### Post by oldcpu on 2007-06-20
> **dannyboy79 said:**
> You can answer your own smart __s question by reading my entire post and not just the last 2 lines.
I have read your (entire) post very well.
> If you missed it than I'll explain it again for you, you can rename a file using the mv command which will get you your tab completion back.
No, you are the one that missed it, twice.  See below.
> If you wanted to know how to rename multiple files than maybe it'd be a good idea to say that next time.
I already know how to rename multiple files.  But this is not about renaming multiple files.  It is about the rename command behaving differently.

Do not use that attitude with me.  You said it yourself that you do not use the rename tool ever.  Yet you still replied.  Maybe you were trying to be helpful by offering an alternative (mv).  But as mentioned, this is not how to rename (multiple) files.

Also, the fact that I know that the rename command behaves differently already hints that I have read the manual.  I felt that you were just knee-jerking that post when you told me to read the manual.

Hey, if I posted a question, that can be easily answered by reading the manual, then I would not mind getting the "RT(F)M."

> **Mr. C. said:**
> Oldpc,

The function I posted is temporary if you enter it into your current shell and use it.  If you want to be able to use it now and in subsequent shells, you can place it in your .bashrc file.  Edit your ~/.bashrc file, and copy/past the code. On subsequent bash shells, the function will be available.

I just copied/pasted the code again too (to ensure I didn't have a typo).  It works just fine.  If you find an error, please show the actual  output on your screen, rather than interpret it and report "it fails".  Exact error messages and output is crucial to getting you the help you desire.

MrC

Okay, thanks again.  Great advice; I will do that in my .bashrc.

Earlier, I tried using it as a bash script, but returned with an "error":
```
bash: Can't rename oldfile: No size file or directory
```
Even though it returned with an error, the files still renamed!  I think the "error" lies in the "$@" part.

---

### Post by Mr. C. on 2007-06-20
Please copy and paste the command you used, and the actual error.  Without seeing the input, I can't diagnose the problem.  And there error you present has a typo: it would have been "No **such** file or directory".

Here is my run, with three files, changing .pdf into .txt.  Two file names have spaces in them, to show how arguments are passed correctly through the function:

```
$ ls -1
a\ a.pdf
b\ \ \ b.pdf
c.pdf

$ myrename .pdf .txt *

$ ls -1
a\ a.txt
b\ \ \ b.txt
c.txt
```

The "$@" means the remaining arguments, all quoted correctly, so that spaces, etc. within file names are not word split.  Otherwise, the file "a b" would end up looking like two arguments "a" and "b" instead.

MrC

---

### Post by oldcpu on 2007-06-21
> Please copy and paste the command you used, and the actual error.
The script that I have used:
```
#!/bin/bash
rename s/$1/$2/ $@
```
Commands I have used and the error:
```
$ ls
oldfile01.foo  oldfile02.foo  oldfile03.foo
$ rename2 old new *.foo
Can't rename old new: No such file or directory
$ ls
newfile01.foo  newfile02.foo  newfile03.foo
```
Before, I used $3 instead of $@, but the 3rd parameter had no effect.  It worked when I substituted the 3rd parameter with a fixed target (*.foo), but then I would have to change the script every time I want to target something different.
> And there error you present has a typo: it would have been "No such file or directory".
Yes, because it was typed off a piece of paper which I wrote the error on.  I was on another system at the time, so I could not copy-and-paste.

In conclusion, your code was better since it did not return with an error.

---

### Post by Mr. C. on 2007-06-21
The script you wrote won't work.  The $@ variable means ALL positional parameters (not all but the first two); additionally, it will fail for any filename with whitespace in the name (eg. "a b").

MrC

---


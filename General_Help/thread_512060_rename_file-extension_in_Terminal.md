---
title: "rename file-extension in Terminal"
date: 2007-07-28
forum: General Help
---

### Post by Thorun on 2007-07-28
I have some files with some different names and without an extension. Now i want to make all those files have the same extension: *.flv
I think it should be do-able in the Terminal like in DOS, where you would write: 
```
ren *.* *.flv
```
and get the job done. 

I'm only a few millimeter from rebooting in Windows and do it with the DOS-prompt - but i refuse. I *want* to learn Linux and get comfortable with the Terminal. 

After searching for a whole day, I didn't come up with something usefull. 
I have read about a programming-language called Perl where the commando should be "rename". 
[http://www.evolt.org/article/Renaming_Files_with_Perl/17/351/](http://www.evolt.org/article/Renaming_Files_with_Perl/17/351/)
[http://mailman.linuxchix.org/pipermail/techtalk/2001-October/009175.html](http://mailman.linuxchix.org/pipermail/techtalk/2001-October/009175.html)
It didn't work. 

I have played a lot with 
```
rename 's/\.inc/\.htm/' *.inc
```
this one renames *.inc files to *.htm-files in a directory. It works like a charm, IF only the file has an extension in the first place. I can't get the "rename" to work, if i have some files without an extension (that i want to give the extension .flv)

I know about the "mv" command in Linux and i can "move" one file to another file. But not a whole bunch of files at one Terminal-command.


If you know how to get the job done, I'm all ears!  :confused:

---

### Post by MrHippocampus on 2007-07-28
Well I found this site which says one way (well, two ways actually) to do it, [link]("http://www.moxleystratton.com/articles/rename-files-bash")

---

### Post by Thorun on 2007-07-28
It's a wery good link. After playing with "section 2" in the link i could make that one work. But not section 1 - which is about renaming the extensions...

After following the three steps (with the ultra-short commandline added) - i get following error:


```
#!/bin/bash

old=foo
new=darkwing
ls *old|sed 's/\(.*\)\.old/mv \1.old  \1.new/'|sh

``````
rune@dell-uff:~/Desktop/testfiles/YouTube Video$ ./renameext.sh
ls: *old: No such file or directory
rune@dell-uff:~/Desktop/testfiles/YouTube Video$ 

```

Now - i don't know why this error occur. But i have tried fixing it for some time now - and still without any luck. 




BUT... !!!!! 111!!!!       :)

I made it work with "rename" aftar all!


```
Terminal-command 	:	 before 	:	 after

rename 's/txt$/html/' *		testfil.txt		testfil.html
rename 's/.txt/.html/' *	restfil.txt		testfil.html
rename 's/$/.flv/' *		testfil			testfil.flv
rename 's/.txt$//' *		testfil.txt		testfil
rename 's/.txt//' *		testfiltxt.txt		testfi.txt
```

---

### Post by catnappist on 2007-08-18
> **Thorun said:**
> rename 's/txt$/html/' *[/CODE]

Thank you, that's what I've been trying to do. Nice and easy!

---


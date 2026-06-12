---
title: "Cat command doesn't seem to be working ..."
date: 2014-08-10
forum: General Help
---

### Post by Lamin on 2014-08-10
I'm currently reading "Assembly Language - Step by Step". In one of the chapters, the author has us download 2 files and open them in Bless.

The file names are 

samwindows.txt 

and 

samlinux.txt 

I was able to download them just fine and opened them in Bless. However, he asked us to use the cat command to compare the output of the two files. I know what the end result should be but when carrying out the exercise I could not produce the expected result. 

When I input "cat samlinux" and "cat samwindows" in the terminal, I got the following:

larinkaare@larinkaare-Inspiron-N4010:~$ cat samwindows
cat: samwindows: No such file or directory
larinkaare@larinkaare-Inspiron-N4010:~$ cat samlinux
cat: samlinux: No such file or directory
larinkaare@larinkaare-Inspiron-N4010:~$ 

Any suggestions? 

Below is some information about cat that might help: 

larinkaare@larinkaare-Inspiron-N4010:~$ whereis cat
cat: /bin/cat /usr/share/man/man1/cat.1.gz

larinkaare@larinkaare-Inspiron-N4010:~$ cat --version
cat (GNU coreutils) 8.13
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Torbjörn Granlund and Richard M. Stallman.

larinkaare@larinkaare-Inspiron-N4010:~$ unalias cat
bash: unalias: cat: not found

larinkaare@larinkaare-Inspiron-N4010:~$ which cat
/bin/cat

larinkaare@larinkaare-Inspiron-N4010:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Thank you in advance for your help.

---

### Post by SeijiSensei on 2014-08-10
You need to use the full filename like samwindows.txt.

You might also find the "more" command a better choice than "cat" when browsing a file from the command prompt.

---

### Post by steeldriver on 2014-08-10
If the file is called samlinux**.txt** then that is exactly what you need to enter - Linux considers samlinux (without the extension) to be a different file

```

cat samlinux.txt

```

Also make sure you are in the directory that contains the file

---

### Post by Lamin on 2014-08-10
Thank you Seij and Steel for your respective responses. 

I originally tried the following variations 

cat Samlinux.txt 
cat samlinux.txt 

cat Samwindows.txt
cat samwindows.txt 

When none of those commands worked, I googled "cat command" and the first few articles I read made it seem like the .txt portion was not necessary, so my apologies. 

Nevertheless, I retried the commands and the results were the same. 

larinkaare@larinkaare-Inspiron-N4010:~$ cat Samlinux.txt
cat: Samlinux.txt: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~$ cat samlinux.txt
cat: samlinux.txt: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~$ cat Samwindows.txt
cat: Samwindows.txt: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~$ cat samwindows.txt
cat: samwindows.txt: No such file or directory

**The following seems promising: **

> Also make sure you are in the directory that contains the file

How do I go about doing this?

I know about cd from messing around with command prompt in windows (Unfortunately the only thing I remember was that the command cd stands for change directory :(  ) but I always assumed terminal in its default setting was able to access files from either C: or  the downloads folder, as two examples. Then again I'm a everything-computer preemie so if I provided you with a facepalm moment I do apologize : ) I may not survive my computer journey but as of right now I am trying. 

The files are under Downloads -> asmsbs3e -> chapter 5.

---

### Post by Lamin on 2014-08-10
Did some light reading and did the following:

larinkaare@larinkaare-Inspiron-N4010:~$ ls -d */
Desktop/    Downloads/  Pictures/  Templates/
Documents/  Music/      Public/    Videos/

larinkaare@larinkaare-Inspiron-N4010:~$ cd downloads/
bash: cd: downloads/: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~$ cd downloads
bash: cd: downloads: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~$ cd Downloads

larinkaare@larinkaare-Inspiron-N4010:~/Downloads$ cat samlinux.txt
cat: samlinux.txt: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~/Downloads$ cat samwindows.txt
cat: samwindows.txt: No such file or directory

It seems that even when I point the terminal toward the Downloads directory (assuming that is what I did), the cat command still does not recognize samwindows.txt or samlinux.txt as files that exist.

---

### Post by JKyleOKC on 2014-08-10
> **Lamin said:**
> The files are under Downloads -> asmsbs3e -> chapter 5.Try these commands:
```
cd $HOME/Downloads/asmsbs3e/chapter\ 5
ls -al
```The first will put you in the directory where the files now reside. The capitalization and the slant of the slashes are both critical; the "$HOME" makes the command start in your home directory. The backslash near the end of the line hides the blank space from the command interpreter which would otherwise interpret the "5" as a separate parameter rather than as a directory name.

The "ls" command simply displays all the content of the current directory; the "-al" parameter tells it to show hidden files and ownership details in addition to just ordinary non-hidden filenames.

If that shows you the files, you can then proceed with use of the "cat" command following the tutorial -- but as has already been said, "less" is easier to use than "cat" in most situations since it pauses at the end of a screenful, like the Windows command "more" does.

In this case, "cat" may be more useful, though, since it won't erase the previous file from the display. If both files are only a few lines, they may both be on screen at the same time which makes it easier to compare them.

---

### Post by oldos2er on 2014-08-10
```
ls
``` should show whether the sam*.txt files are in the current directory or not.

For a beginner's tutorial to using the terminal, click the PDF download link in my sig. It is time well spent if you have a desire to learn.

---

### Post by Lamin on 2014-08-10
O'k, finally solve it. 

It had the potential to be a pain in the ass though, given my lack of knowledge. Lucily I did ls -d */ one more time and was on my way. 

My question is, Downloads seems to be under Home Directory, which I assume is the terminal default setting. How can I streamline this process without having to utilize the cd command prompt x amount of times, or is there no way to avoid what I will paste down below. Once again, thanks for your help. 

larinkaare@larinkaare-Inspiron-N4010:~$ cd Downloads

larinkaare@larinkaare-Inspiron-N4010:~/Downloads$ cat samlinux.txt
cat: samlinux.txt: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~/Downloads$ cat samwindows.txt
cat: samwindows.txt: No such file or directory

[B]larinkaare@larinkaare-Inspiron-N4010:~/Downloads$ ls -d */
asmsbs3e/[/B]

larinkaare@larinkaare-Inspiron-N4010:~/Downloads$ cd asmsbs3e

larinkaare@larinkaare-Inspiron-N4010:~/Downloads/asmsbs3e$ cat samwindows.txt
cat: samwindows.txt: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~/Downloads/asmsbs3e$ cat samlinux.txt
cat: samlinux.txt: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~/Downloads/asmsbs3e$ ls -d */
chapter10/  chapter11/  chapter12/  chapter5/  chapter7/  chapter8/  chapter9/

larinkaare@larinkaare-Inspiron-N4010:~/Downloads/asmsbs3e$ cd chapter 5
bash: cd: chapter: No such file or directory

larinkaare@larinkaare-Inspiron-N4010:~/Downloads/asmsbs3e$ cd chapter5

larinkaare@larinkaare-Inspiron-N4010:~/Downloads/asmsbs3e/chapter5$ cat samlinux.txt
Sam
was
a
man.

---

### Post by steeldriver on 2014-08-10
Really this is no different from Windows cmd.exe

You don't need to cd to the directory if you give a complete (relative or absolute) pathname to the file

```

cat ~/Downloads/asmsbs3e/chapter5/samlinux.txt

```

Or if you prefer you can use cd - but jump straight to the target directory

```

cd ~/Downloads/asmsbs3e/chapter5
cat samlinux.txt

```

In either case, you can use **tab completion** to cut the amount of actual typing to almost nothing

---

### Post by Lamin on 2014-08-10
Thank you JKyle and Oldos for your contributions. 

I saw both of your posts after I had posted my last one. 

Kyle, 

for some reason 

1) cd $HOME/Downloads/asmsbs3e/chapter\ 5  

did not work but 

2) cd $HOME/Downloads/asmsbs3e/chapter5 

did. 

After 2, I was able to use the ls command and needless to say I was happy. 

I guess if I want to use the cat command I just have to know the path of the file. It also solves my "ls -d */ x amount of times" question. I'll look into the less command for the future.

Oldos, 

I'm really grateful for the link. I downloaded the file. It's hefty but I imagine studying this now will save me a lot of frustration down the line : ) 

Once again, I want to thank everyone for all thier help.

---

### Post by JKyleOKC on 2014-08-10
You're quite welcome -- and by the way, welcome to the wonderful world of Linux!

If you're familiar with the CMD capability of Windows, you'll find that the command-line interface in this new universe works in much the same way, but is much more powerful. For one thing, here we have the ability to choose from several command interpreter programs rather than just a couple. The one that comes by default in most if not all flavors of Ubuntu is called "bash" which stands for "Bourne Again SHell" (and there's no relation to the series of thriller novels; a fellow named Bourne was one of the very early developers). The original Unix command interpreter was simply "sh" for SHell, called that because it surrounded all the commands much like a nut's shell surrounds its meat.

As you gain familiarity with the system, you can dig into the capabilities of bash; there's been at least one large book written about it and it's well worth having a copy on hand. Although I've worked with related systems since the early 1970s and even wrote the chapters about command interpreters in the ancient "MS-DOS Encyclopedia" and the later "Undocumented DOS," I keep my copy of "Learning the bash Shell" (ISBN 1-56592-347-2) next to my keyboard for easy reference!

---

### Post by SeijiSensei on 2014-08-10
A couple of other things to keep in mind:

First, *nix systems are case sensitive.  The name "Samwindows.txt" is not the same as "samwindows.txt."  Also when you wrote
> The files are under Downloads -> asmsbs3e -> chapter 5
Jim Kyle reasonably inferred that the directory was named "chapter 5" not "chapter5".  Those are not the same on *nix systems either.  If you do have files with embedded spaces in their names, I find it easiest to wrap the file names in single quotes like this
```
more '/path/to/some/file/with/embedded spaces'
```
but you can also "escape" the space with the backslash character "\ " as Jim did above.

The best way to find files quickly from the command line is to use "locate filename".  You can also give locate a string like "sam" to find all the files with "sam" in their names.

---


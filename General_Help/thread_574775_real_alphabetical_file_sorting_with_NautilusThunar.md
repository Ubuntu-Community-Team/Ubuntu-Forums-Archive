---
title: "*real* alphabetical file sorting with Nautilus/Thunar."
date: 2007-10-13
forum: General Help
---

### Post by EZ81 on 2007-10-13
Hello.

Is there a way to get Thunar (or Nautilus, if necessary) to stop messing up the sort order?

If i have a bunch of files like this:
```
$ ls | cat
002
01
03
1
```
and i look at the folder in thunar (or nautilus, both with xfce and 6.06), it sorts them like this:
```
1
01
002
03
```
which is a nice try, but if needed i can add leading zeros myself, thanks a lot,  i'd rather have the file manager do what it says it does, which is alphabetical file order (like ls and every other apllication in the world does), not guessing the order based on some numbers  and getting it wrong :mad: Adding a leading dummy letter to each filename did not help. 

Is there an alternative file manager that works well with xfce (meaning: not rox-filer or xffm) which does not have this "intelligent" sorting feature? Or is there a (very well hidden) way to disable this in thunar?

I have a folder with a mess of text files that are named like above and i'd really like to do some manual moving/deleting with the mouse for various reasons. If repairing the sort order in thunar is impossible, no problem, but if there is a hidden option that says "[x] enable intelligent file sorting", i'd like  to find it ;).

Regards,
Matthias

Excuse the rant. I am a firm believer in that if an ancient standard gets cleverly improved (and in many cases this number thing is an improvement, at least for beginners), there needs to be a way to do it the simple, dumb and predictable old way.

---

### Post by nick_h on 2007-10-13
Have you looked in the gconf-editor under /apps/thunar ?

I have looked under nautilus and can't find any options for sort order except for the column to sort.

---

### Post by EZ81 on 2007-10-13
Thanks Nick,
I had never even noticed the gconf-editor before (after +1year of Dapper Drake usage), good to know this. Thunar is not even in there on my system (i did the standad ubuntu install and installed xfce later), though. However, I doubt Thunar has more options than Nautilus, as they actually mention its lack of configurability as a feature on the XFCE site. I guess I'll just have to live with this...

Thanks again,
Matthias

---

### Post by natirips on 2008-04-10
(I couldn't stop myself from digging this up.)

I have the same problem, for example, I made three files like this
```
natirips@natirips-laptop:~/Radna površina/bezimena mapa$ touch 1
natirips@natirips-laptop:~/Radna površina/bezimena mapa$ touch 0
natirips@natirips-laptop:~/Radna površina/bezimena mapa$ touch 01
natirips@natirips-laptop:~/Radna površina/bezimena mapa$ ls
0  01  1
natirips@natirips-laptop:~/Radna površina/bezimena mapa$ 

```So, "ls" sorts them perfectly, but Nautilus will put this "01" file after the "1" file. So in Nautilus they are sorted like "0", then "1", and then "01" at the end!:(
I'm using Ubuntu 7.10 and Nautilus 2.20.0 . I checked the "gconf-editor" for Nautilus settings and couldn't find a way to undo it's *intelligence*.
[B]
And I ask, is there really no way to undo the "intelligent" file sorting in Nautilus??[/B] It's really frustrating...

---

### Post by zvacet on 2008-04-10
```
man sort
```

---

### Post by ryanhaigh on 2008-04-10
How does sort help with the problem at hand? This is a rather annoying 'feature' of nautilus. It would be nice if leading punctuation would also place a item at the top of the list. Has anyone searched ubuntu brainstorm?

---

### Post by natirips on 2008-04-11
> **zvacet said:**
> ```
man sort
```'sort' command sorts lines within a text file (from 'man sort'):```
SORT(1)                          User Commands                         SORT(1)

NAME
       sort - sort lines of text files

SYNOPSIS
       sort [OPTION]... [FILE]...

DESCRIPTION
       Write sorted concatenation of all FILE(s) to standard output.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.  Ordering options:

       -b, --ignore-leading-blanks
              ignore leading blanks

       -d, --dictionary-order
              consider only blanks and alphanumeric characters

       -f, --ignore-case
              fold lower case to upper case characters

```It has nothing to do with file sorting within Nautilus...:(

---

### Post by natirips on 2008-04-13
If things don't change in Hardy, I guess I'll just have to modify and compile Nautilus myself...:(

---

### Post by natirips on 2008-05-09
I've found a program that sorts files properly, although it doesn't look as nice as Nautilus, it's called "GNOME Commander" (I've found it in the Add/Remove programs accidentally). It's not a solution for this problem, but it sorts properly and has most of the functions that Nautilus has (with exceptions like icon viewing).

---

### Post by EZ81 on 2008-05-15
Thanks, natirips.

There is also **xfe** (at least on debian), which looks pretty much like the Windows Explorer used to and which also gets the sorting right. And it is waaaayyy faster than nautilus on my old PC :)

Matthias

---

### Post by wheezer on 2008-07-17
I found this discussion of the problem
[http://ubuntuforums.org/archive/index.php/t-471154.html](http://ubuntuforums.org/archive/index.php/t-471154.html)

I find it uncanny that there is no official discussion of this. I have never seen this behavior in any file system anywhere, and we all have to put up with it why?  Some call it a bug, others a feature.  I just want my damn files to sort as I expect, and there doesn't seem to be any solution.  I hate this side of Linux and Ubuntu with a passion.

---

### Post by natirips on 2008-07-17
I've noticed that, in large directories with thousands of files, at first it acctually sorts them alphabetically as one would expect, but then it starts scrambling the order madly. :? TT

---

### Post by wheezer on 2008-07-17
> **natirips said:**
> I've noticed that, in large directories with thousands of files, at first it acctually sorts them alphabetically as one would expect, but then it starts scrambling the order madly. :? TT

I wish someone would do a "common annoyances and tweaks" section of this site, where fixes for this stuff can easily be located, OR definitive reasons why they are not possible. I am still not convinced there is not a fix for this problem.

---

### Post by natirips on 2008-07-17
Wheezer pointed to a thread that said the following:> I saw that. At first I thought that it WAS a bug because I put the locale setting in .bashrc, but Nautilus did not respect it. On further inspection, it seems that .bashrc is for interactive shell-based stuff only, so it makes sense that Nautilus wouldn't read its settings. It DOES, however, work if you put export LC_COLLATE=C into .gnomerc and restart. There's probably a more proper place for this setting (wherever system-wide user settings should go), but .gnomerc does the trick.

EDIT: Note that this will tell Nautilus to use ASCII sort order. Meaning files will be ordered first by (most) special characters, then uppercase characters, then lowercase characters. This is, I believe, the old school Unix way of doing things, but it is NOT the Windows way of doing things. Windows sorts by special characters, then by normal characters, case-insensitive. ASCII sort takes case into account. Personally that's what I prefer, but it may not be what other people are expecting.

So, where is that .gnomerc file? I couldn't find it either in my home directory or in /etc...

---

### Post by wheezer on 2008-07-18
> **natirips said:**
> Wheezer pointed to a thread that said the following:
So, where is that .gnomerc file? I couldn't find it either in my home directory or in /etc...


I couldn't find it either.  It's soooooooo annoying. The entire issue.

---

### Post by natirips on 2008-07-18
I am currently downloading 32-bit Fedora (I had 64-bit one before, but it doesn't work with VirtualBox), so I will be testing Nautilus on Fedora when it downloads just to see if different distro/locale settings will maybe change something/anything...

---

### Post by natirips on 2008-07-18
So I tested Fedora 8's Nautilus, and here are results:

========CONSOLE
[natirips@localhost test]$ ls -1
0
00
000
001
002
003
01
02
03
1
2
3
4
[natirips@localhost test]$ 
========
Ok, now that's what one would expect, that's normal way of sorting and I have no complaints about that. Ubuntu 8.04's console does the same.

=========NAUTILUS
0
00
000
1
01
001
2
02
002
3
03
003
4
=========
Why would I bother putting leading zeroes if I wanted them ignored? Moreover, "01" should come before "1", not after it! It's all scrambled and locally twisted upside down... oohh :(. TT =(

I'll be attempting usage of Konqueror under Gnome and report results later, maybe tomorrow (because I'm too frustrated now).

This is a serious security vulnerability bug which may lead to complete system destruction and hardware damage due to a frustrated user throwing their computer through the window. So if someone doesn't feel sory for that user, at least one could feel sory for the poor computer...

Edit: Just tried English(US) version on Fedora (It's easy to switch languages on Fedora), does the same thing.

---

### Post by natirips on 2008-07-18
Ok, I recovered from all the frustration after a nice cup of tea, so I tested Konqeror today, here are results:

On Ubuntu 8.04 (with Gnome):
=======Terminal:
natirips@natirips-laptop:~/Desktop/test$ ls -1
0
00
000
001
002
003
01
011
012
013
02
03
1
10
11
110
111
112
12
2
3
natirips@natirips-laptop:~/Desktop/test$ 
=======Nautilus:
0
00
000
1
01
001
2
02
002
3
03
003
10
11
011
12
012
013
110
111
112
======Konqueror:
0
00
000
001
002
003
01
011
012
013
02
03
1
10
11
110
111
112
12
2
3
===========
So Konqueror sorts just fine! I've found my sollution/substitution for Nautilus (which completely messed-up the order):D. <So happy!>.

And by-the-way, a little side-story:
When i installed Fedora in VirtualBox, I thought how nice it would be to install Guest Additions (to enable mouse pointer integration/copy paste sharing/...). So I run the installer from the console. It told me I have to be root to do that, what was to be expected. So I started it with sudo, and guess what it told me! It said "natirips is not in the sudoers file.  This incident will be reported.". I loled so hard, to whom will I be reported? To myself? Lol. It's gonna say: "Hey natirips, natirips tried to locally hack into his own computer, go punish him/yourself for that!". Rofl.:lolflag: At very least, Fedora's got a good sense of humor.

---


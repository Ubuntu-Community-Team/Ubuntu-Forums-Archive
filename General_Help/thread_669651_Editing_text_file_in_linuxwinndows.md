---
title: "Editing text file in linux/winndows"
date: 2008-01-16
forum: General Help
---

### Post by Howard Kaikow on 2008-01-16
*ix uses hex 0A as a line terminator,
When opening such a file in, say, Wordpad, Windows converts the 0A to 0D 0A, and might mess with other stuff.

My failing memory seems to recall a prog that runs in Windows that will preserve the formatting.

Anybody recall the program?

When editing the file in windoze, I need to preserver the linux format effectors.

---

### Post by mbaucsoft on 2008-01-16
While it may not be very popular on Windows machines, I believe Emacs will keep the end of line characters.

You could also try file converters such as the one from GNU win32:

[http://gnuwin32.sourceforge.net/packages/cygutils.htm](http://gnuwin32.sourceforge.net/packages/cygutils.htm)

---

### Post by rocketman768 on 2008-01-16
You want the tofrodos package I think. Use "sudo apt-get install tofrodos" and you will then have two programs called todos and fromdos. If you want to convert f.txt from dos format to unix format, just type "fromdos f.txt". Opposite goes for todos.

---

### Post by Howard Kaikow on 2008-01-16
> **mbaucsoft said:**
> While it may not be very popular on Windows machines, I believe Emacs will keep the end of line characters.

You could also try file converters such as the one from GNU win32:

[http://gnuwin32.sourceforge.net/packages/cygutils.htm](http://gnuwin32.sourceforge.net/packages/cygutils.htm)


Thanx.

I used to use JED back in Windows 95/98.
Might work in Windows 2000 as well.

---

### Post by Howard Kaikow on 2008-01-16
> **rocketman768 said:**
> You want the tofrodos package I think. Use "sudo apt-get install tofrodos" and you will then have two programs called todos and fromdos. If you want to convert f.txt from dos format to unix format, just type "fromdos f.txt". Opposite goes for todos.

THanx.

I need to do this from within windoze.

---

### Post by capink on 2008-01-16
Scite has an option to use either unix or windows line end. The program is available linux and windows as well.

---

### Post by p_quarles on 2008-01-16
> **capink said:**
> Scite has an option to use either unix or windows line end. The program is available linux and windows as well.
There's also Notepad++, which is a fork of SciTE, and imho the best text editor designed for Windows.

---

### Post by Howard Kaikow on 2008-01-16
THanx.

I've downloaded

Notepad++
Scite
Programmer's Notepad

Now to decide which to try.

---

### Post by NGSG on 2008-01-17
you could use emacs for both windows and unix and then tell emacs:
M-x set-buffer-file-coding-system 
type enter
and then give
 undecided-unix
then your file is portable from one OS to the other one.
hope this helps.

---

### Post by Howard Kaikow on 2008-01-18
Thanx to those responding.

Here's what I decided.

From about 1993 to 1998, I used JED on both unix and windows 95/98.
I prefer to not use an emacs interface..

So, I installed Notepad++ and Programmer's Notebook.

For the purposes of the problem I raised in this thread, I decided that Notepad++ was "better".

Anybody know how to shut  off the Recent Files kist in Notepad++?

I tried registering at SourceForge so i could ask in the Notepad++ forum, but the forum sets up my accont and does not accept the password, despite restting thru the normal mechanism.

---


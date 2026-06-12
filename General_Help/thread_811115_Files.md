---
title: "Files"
date: 2008-05-28
forum: General Help
---

### Post by Seth x Limit on 2008-05-28
I am new to the Ubuntu OS.
I switched from Windows XP SP2 today.

I was wondering, what do I need to run .exe, .so files and etc.

I was trying to install a few things and it will not automatically run them.


thanks in advance.

---

### Post by Seth x Limit on 2008-05-28
Anyone?

---

### Post by cosine352 on 2008-05-28
you need wine.
> sudo apt-get install wine

try to use alternative applications of windows for Ubuntu

---

### Post by Seth x Limit on 2008-05-28
Well, that's not exactly what I meant, at least I think.

Whenever I click a .exe file it doesn't work, It will bring up something to open it, but it won't let me run the file.

I tried the 'wine' program but when I installed the .exe file, it will blink and come up, but automatically close.

---

### Post by cosine352 on 2008-05-28
probably the application is not wine compatable. you can find it out here
[http://www.winehq.org/]("http://www.winehq.org/")

what is the output of 
> wine "filename.exe"

---

### Post by bingoUV on 2008-05-28
> **Seth x Limit said:**
> Well, that's not exactly what I meant, at least I think.

Whenever I click a .exe file it doesn't work, It will bring up something to open it, but it won't let me run the file.

I tried the 'wine' program but when I installed the .exe file, it will blink and come up, but automatically close.

1. How did you install the .exe file?

2. Is it necessary to use the .exe file? Are you sure there is no native linux program that performs the same task as well as the .exe, or better? Look at [http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

### Post by Seth x Limit on 2008-05-28
well, I'm downloading AOL Instant Messanger.

I don't want to use the one pre-installed

and when I open up the installer, for linux. (.exe)

It doesn't work.

---

### Post by bingoUV on 2008-05-28
> **Seth x Limit said:**
> well, I'm downloading AOL Instant Messanger.

I don't want to use the one pre-installed

and when I open up the installer, for linux. (.exe)

It doesn't work.

The installer for linux is .exe?

---

### Post by Seth x Limit on 2008-05-28
That is what it is giving me.

---

### Post by bingoUV on 2008-05-28
[http://www.aim.com/get_aim/linux/latest_linux.adp#install](http://www.aim.com/get_aim/linux/latest_linux.adp#install)

Try the deb. If it does not work, try tgz.

---


---
title: "Error when installing programs"
date: 2008-04-26
forum: General Help
---

### Post by Butlero on 2008-04-26
Ok, I'm a newbie to linux ubuntu and keep getting the same error when installing anything really, I've tried programs and Firefox plug ins and no results.

Here is the error:>  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've run what it says in the terminal then I get this: > user@user -desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Can anybody help me with this? I am running Ubuntu 8.04 installed through wubi.

---

### Post by ludovicc on 2008-04-26
You need to run dpkg with sudo, it will grant you the superuser privilege:

sudo dpkg --configure -a

Then sudo will as for a password, enter your user password. 
It's a bit strange that you are working with the command line, normally to install applications you can use Add/Remove programs at the botton of your Applications menu, or Synaptic package manager in the System/Administration menu.

Hope this helps,
Ludovic

---

### Post by Butlero on 2008-04-26
Done that but when I try to type my password in it doesn't type...

---

### Post by Butlero on 2008-04-26
Can anybody help?

---

### Post by RichardG891 on 2008-04-26
In terminal the password is blanked (no echo) so you don't even get asterisks shown.... type it in anyway and enter.... and the cursor line will change from your username to "root".

---

### Post by Butlero on 2008-04-26
Thanks for your help guys, I can finally install programs!

---

### Post by dubdave on 2008-04-26
hi guys im kinda getting the same problem i cant open any of my bin files that i download its says i need an application to open it could somebody please help

---

### Post by ludovicc on 2008-04-26
Which bin files? Do you try to run some Windows .exe programs? Those won't work on Ubuntu, unless you install Wine, but it's not trivial to use. Can you give more detail here, what are you doing exactly?

---

### Post by dubdave on 2008-04-26
well ive tried to download itunes and a cdmixer ect it downloads but i cant open them

---

### Post by ludovicc on 2008-04-26
Itunes doesn't work under Linux, but there are sereval applications which you can use to play your music (but probably not the DRM music which you bought on ITunes music store). Try Rhythbox (already installed in Ubuntu, in the Applications/Sound and Video menu), or XMMS, or Amarok. All those applications can be easily installed by going to the Applications menu, select Add/remove..., and then select the applications to install. You don't have to go to the internet and download applications manually, all is done for you.

To burn CDs, you can use Brasero.

---

### Post by dubdave on 2008-04-26
cheers so is there no way of checking for applications to open any of the files i have downloaded sorry im very much a novice

---

### Post by JimmyHopkins on 2008-04-26
"cheers so is there no way of checking for applications to open any of the files i have downloaded sorry im very much a novice"

No, but you can try searching the file extention (ie mp3, pdf, rar, cbr, etc.) in add/remove programs will usually find something that can open it. Give an example of something you cannot open (besides .exe).

---

### Post by dubdave on 2008-04-26
well most of the things that i have downloaded have exe at the end of them does that mean i cant use them

---

### Post by ludovicc on 2008-04-26
Read this first: Linux is not Windows!
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

In Windows, programs work in a certain way, and they end with the .exe extension. But Windows programs cannot work under Linux, just as they cannot work under OS X (the Apple system). It's a bit like playing with Legos made by 2 different companies, they won't fit together.

Actually, the situation is not so bad, and you can run Windows programs under Ubuntu, but it's not easy and requires you to install a software called 'Wine'. I can't help you further, because it's something that's I have not used for a long time, and it doesn't work very well. Anyway, if you need to use Windows programs, post on the forum about how to use Wine.

Ludovic

---


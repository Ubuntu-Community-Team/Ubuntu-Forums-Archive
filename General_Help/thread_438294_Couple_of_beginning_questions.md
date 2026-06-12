---
title: "Couple of beginning questions"
date: 2007-05-09
forum: General Help
---

### Post by rules on 2007-05-09
Hi all

I installed Feisty Fawn a couple of days ago and have played around with it a bit. There are a couple of things I still need to accomplish before I can permanently move away from Win, so here goes.

1. Is there a way of importing mail from Outlook to Evolution Mail?
2. I loaded Wine but have no idea how to use it. I need to install 1 or 2 win applications and need to run 1 dos executable (doesn't install). How would I go about it?

Thanks.

---

### Post by rax_m on 2007-05-09
Hi 

Here's some links to some HOW TO's

1. [http://ubuntuforums.org/showthread.php?t=91687&highlight=import+outlook+mail](http://ubuntuforums.org/showthread.php?t=91687&highlight=import+outlook+mail)
2. For wine, I'm assuming you've already installed it using the Add/Remove application. Then at a command prompt time in "wine <path to program you want to run>" ( without the quotes) and that should execute the windows program. 
As for the DOS program, if it doesn't work on wine, you could use something like DOSEMU with Freedos

Hope that helps.. DISCLAIMER: I'm not an expert so you'll have to do all the reading yourself ;)

Rax

---

### Post by rules on 2007-05-10
Hi 

Thanks for the help so far, sorted out my mail already.

As for Wine, I tried installing an app, but it complained about a missing .dll which I found on my Windows partition but I have no idea of where Wine creates its virtual windows. Any ideas?

Thanks again.

---

### Post by kragen on 2007-05-10
Look under ~/.wine/dosdevices for the wine windows directory 

What was the missing .dll? The chances are its probably one of a long string of missing .dll's from something like the .net framework. It's worth seeing if you cant figure out what it is and download the installer instead you can install the .net framework in wine with very little hassle - just download and run the installer from the microsoft site :D - I'm not even sure that copying .dll's from windows to wine works.

---

### Post by nerdman978 on 2007-05-10
1. Yes Evolution has an option to do that last time I checked.
2. If you've installed Wine, try to open the Windows ".exe" executable files by right clicking and hitting "Open with Wine windows emulator".

---

### Post by rules on 2007-05-10
if memory serves it was dsapi.dll

---

### Post by rules on 2007-05-10
sorry for my ignorance but, where would I find /.wine/dosdevices

Does it make a difference that I'm logged on as root?

Even with dosemu I can't seem to find the location of the folders as directed in the read-me's

---


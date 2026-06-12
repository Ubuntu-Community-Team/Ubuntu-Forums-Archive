---
title: "i got wine, how do i launch a program?"
date: 2007-05-25
forum: General Help
---

### Post by powerplayground on 2007-05-25
I know you have to do it in the command line, and i know how to type it, but the website is telling me to type it out with the drive letters. What im wondering is how would i do this if linux has no drive letters like xp does. Im in root and the setup.exe file is in a folder on the desktop. What do i typoe in the command line?

---

### Post by aysiu on 2007-05-25
Read this:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by powerplayground on 2007-05-25
i got it to run, but now it wont run because "jscript" is not properly registered. Any ideas?

---

### Post by aysiu on 2007-05-25
What's the program?

---

### Post by powerplayground on 2007-05-25
adobe photoshop cs3

---

### Post by aysiu on 2007-05-25
Good luck. As far as I know, that doesn't work in Wine.

More details here:
[http://appdb.winehq.org/appview.php?iVersionId=6584](http://appdb.winehq.org/appview.php?iVersionId=6584)
[http://appdb.winehq.org/appview.php?iAppId=20](http://appdb.winehq.org/appview.php?iAppId=20)
[http://appdb.winehq.org/appview.php?iVersionId=5695](http://appdb.winehq.org/appview.php?iVersionId=5695)

---

### Post by powerplayground on 2007-05-25
that sucks. I cant even run cs2 :( And let me tell you gimp is no replacement to photoshop :P

---

### Post by aysiu on 2007-05-25
> **powerplayground said:**
> that sucks. I cant even run cs2 :( And let me tell you gimp is no replacement to photoshop :P
[This](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/) *might* help. Not 100% sure on that, though.

---

### Post by powerplayground on 2007-05-26
ill try that, now im wondering how to kill a program in wine that is freezing or is unable to close.

---

### Post by aysiu on 2007-05-26
```
killall wine
``` should do it.

---

### Post by powerplayground on 2007-05-26
hmm i got a stuck window the command says no processes killed and the window is still there. any ideas?

---

### Post by aysiu on 2007-05-26
Alt-F2 ```
xkill
``` Then click the hanging window with your mouse cursor (which should have turned into a skull and crossbones).

---

### Post by powerplayground on 2007-05-26
ok now im having a real big problem. I cant see the .wine direcotry in my user folder. Any ideas on how to unhide everything?

---

### Post by aysiu on 2007-05-26
> **powerplayground said:**
> ok now im having a real big problem. I cant see the .wine direcotry in my user folder. Any ideas on how to unhide everything?
Have you tried Control-H?

Or, if you're using Kubuntu, Alt-V, then H.

---

### Post by Lucifiel on 2007-05-26
If you are using Nautilus and want to view all hidden folders permanently, then try :

In Nautilus, go to Edit ===>Preferences. Then under "View" tab, check "Show hidden and backup files".

---

### Post by powerplayground on 2007-05-26
got that part down but that guide is terrible. Im stuck on this part:

The next step is to copy that file to your Ubuntu box and convert it to the encoding of YOUR system. For example, if your Ubuntu box has as default charset ascii and your Windows box has ucs-2 then “$ recode ucs-2..ascii adobe.reg” would do the trick. After you converted your adobe.reg file, type “$ sudo wine regedit adobe.reg” to import it to wine.

I try the recode command and i placed the file in the deskyop and the root, I pointed to it, and still nothing. any ideas on what to type to point to the file.

---

### Post by aysiu on 2007-05-26
Unfortunately, no. I dug that guide up through a Google search. But I've never installed any Adobe CS in Wine myself.

---

### Post by powerplayground on 2007-05-26
ok how would i kill a certain program in wine. I am patching another program and xfire is stuck on all 4 panels right in the middle.

---

### Post by aysiu on 2007-05-26
> **powerplayground said:**
> ok how would i kill a certain program in wine. I am patching another program and xfire is stuck on all 4 panels right in the middle.
See [post #12 of this thread](http://ubuntuforums.org/showpost.php?p=2725022&postcount=12).

---

### Post by powerplayground on 2007-05-26
tried that worked for my first window but not xfire. Xfire dosent have a bar on top of it. :(

---

### Post by mailbox on 2007-05-26
or run xkill

---


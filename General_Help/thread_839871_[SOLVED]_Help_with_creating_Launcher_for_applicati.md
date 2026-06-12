---
title: "[SOLVED] Help with creating Launcher for application in Wine"
date: 2008-06-24
forum: General Help
---

### Post by brett123 on 2008-06-24
NOT SOLVED YET - I PUSHED THE WRONG BUTTON


I have a unique Windows application, which unfortunately I cannot name here, but please help me if you can.

I have put all the files in one directory in my /home, which includes a couple of .exe files, numerous .dat files, and an .ini file.

The main file to execute is ABC.exe, which if I open this directory and double click ABC.exe then it all works perfectly. The Properties for ABC.exe indicate "Open With Wine Windows Emulator".

All I want to do is create a Launcher on the desktop, yet whatever I do I get "_Cannot find the file ABC.ini in the Working Directory_" error.

**It's this "working directory" I don't know what to do about.** I just can't find anywhere to enter a working directory.

Additionally:
- Make Link also produces the same error
- The "shortcut" doesn't appear in the Wine list under Applications
- there is no install routine for this, just dump the files, and run .exe

Any thoughts?

---

### Post by brett123 on 2008-06-24
As a thought - do I have to move the files from where they are /home/brett123/Documents/ABC/ and put them in some "system directory"???

I'm still stuck in MS Windows habits, and am not used to Linux file systems yet. I'm trying though. :D

---

### Post by VMC on 2008-06-24
> **brett123 said:**
> As a thought - do I have to move the files from where they are /home/brett123/Documents/ABC/ and put them in some "system directory"???

I'm still stuck in MS Windows habits, and am not used to Linux file systems yet. I'm trying though. :D

You can put the apps anywhere. Does this abc.exe app installable, or is it just an executable file? Does it rely in libary or DLL files?

---

### Post by brett123 on 2008-06-25
No install, just the .exe and everything it needs is in the directory. There would be no external .dll or anything I believe.

---

### Post by VMC on 2008-06-25
> **brett123 said:**
> No install, just the .exe and everything it needs is in the directory. There would be no external .dll or anything I believe.

Go here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Search for "Shell Script Installer" then read from there a couple of alternatives making shortcuts and launchers.

---

### Post by brett123 on 2008-06-25
Thanks for that, however I still get the same error even introducing "wine /path/exe" to the launcher.

I then tried moving the directory to the Wine "C: drive" and it still didn't work.

I know this is a Wine issue, so will concentrate my Googles on that now and see how I go.

---

### Post by VMC on 2008-06-25
Can you try another launcher using a simple exe file, like one of the games. For example freecell.exe. See if that works.

---

### Post by brett123 on 2008-06-25
Tried notepad.exe (has no dependencies) and it works fine, can create launchers everywhere.

In my Googling, found this which tends to imply it is a BUG, although I don't have enough knowledge to fully understand what they are saying. It might already be fixed, but maybe I don't have the fix????

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/236106](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/236106)

---

### Post by brett123 on 2008-06-25
BROADENING SCOPE OF THIS QUESTION

Ok, so it seems there is a bug in Wine and it won't set/keep the path if executed from outside the .exe directory.

So I created this (keeping in mind I have no idea what I'm doing here):

#!/bin/bash
cd /home/brett123/.wine/drive_c/ABC/
wine /home/brett123/.wine/drive_c/CIS/abc.exe

- saved that on Desktop as ABC no extension
- chmod 775

It *does* work, runs the .exe file perfectly fine. However, I get this now:
**Do you want to run "ABC" or display its contents? ABC is an executable file.**

I'm hoping this is more of a Linux issue and nothing to do with Wine, hence hoping someone here can help me. I've never written a script before, so I'm doing something stupidly wrong for sure.

---

### Post by VMC on 2008-06-25
> **brett123 said:**
> Tried notepad.exe (has no dependencies) and it works fine, can create launchers everywhere.

In my Googling, found this which tends to imply it is a BUG, although I don't have enough knowledge to fully understand what they are saying. It might already be fixed, but maybe I don't have the fix????

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/236106](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/236106)

So you moved your abc.exe and its support files to one directory and made a launcher that points to that directory, but still it doesn't work. Did you try executing the file inside a Terminal, like so: wine ~/home/abcdirectory/abc.exe. Or better yet, cd to the directory and type wine abc.exe, then what is the error output.

Also here is some reading about what someone has learned regarding Wine. It may have a solution for you:
[http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

---

### Post by brett123 on 2008-06-25
VMC, thank you for persevering with me here, much appreciated.

Hope you saw my last post, we posted at same time as each other.

Running wine ~/home/abcdirectory/abc.exe in a terminal produces the same "can't find .. in working directory" error.

It seems the issue is with Wine. If you navigate to the directory and double click the .exe then Wine uses that directory you are in. However, if you create a Launcher and execute from a terminal (assuming you are NOT in that directory) then you get the same error "can't find .. in working directory".

---

### Post by brett123 on 2008-06-25
And to answer another question you asked me:

Yes, IF you cd to the directory, then run the wine ....exe in a terminal it DOES work.

---

### Post by brett123 on 2008-06-25
> **VMC said:**
> Also here is some reading about what someone has learned regarding Wine. It may have a solution for you:
[http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

Just read all that, and yes it is as we concluded above: you have to first CD to the directory beforehand.

They suggested a workaround like I wrote above - a script to CD first, then execute the .exe, but even when I follow their solution I still get the "this is an executable text file, do you want to run or open" (whatever it is exactly).

Looks like the answer is just in my learning to run a script properly.

Sorry for the triple post, each post was a different topic, will watch myself in future.

---


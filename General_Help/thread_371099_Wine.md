---
title: "Wine"
date: 2007-02-26
forum: General Help
---

### Post by Orfeus on 2007-02-26
I am trying to install rct3 on linux but i keep getting this
```

wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found
```

what do i have to do???

---

### Post by chggr on 2007-02-26
You shouldn't use wine to install Windows applications on linux. It simply won't work...

Instead you can try finding the equivalent of this Windows Software in Linux.
Check this out:
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by Shay Stephens on 2007-02-26
> **chggr said:**
> You shouldn't use wine to install Windows applications on linux. It simply won't work...
Ehhhh, that is what wine is for.  Installing and running windows applications in linux.

I use wine to run Photoshop 7 and it works.  The one thing I noticed about the error message was the double backslashes.  I don't know how you are trying to run the program, but there should only be single backslashes, for example:
c:\windows\system32\setup.exe

Not every program works with wine yet, but each wine release gets better and better.  Assuming the program you are trying to run is Roller Coaster Tycoon 3, it doesn't have an entry in the wine database showing it is working yet.  I don't know what version of wine you are using, but the current version is .9.31.  You can run at the terminal:
```
wine --version
```
to find out what version you are running.  If it is older than the newest version, try upgrading wine and try the install again.

---

### Post by Patrick K on 2007-02-26
I've not installed a lot of programs in wine but I usually run "winefile" then locate the install exe and run it from inside winefile. Might be worth a try.

---

### Post by zanglang on 2007-02-27
You might just be missing Microsoft Windows Installer or InstallShield (can't remember what it was). Try getting Winetools and set up your .wine folder accordingly to get all usually needed components?

---

### Post by chggr on 2007-02-27
> **Shay Stephens said:**
> Ehhhh, that is what wine is for.  Installing and running windows applications in linux.

That's true, but according to my experience the installation of Windows programs under linux using wine rarely succeeds.

---

### Post by Shay Stephens on 2007-02-28
> **chggr said:**
> That's true, but according to my experience the installation of Windows programs under linux using wine rarely succeeds.

But wine is not static, they are improving every month.  There are a number of programs that don't install or run correctly, but every month that changes.  So a blanket statement doesn't really fit.  Just because it didn't work in the past doesn't mean it won't work now :) 

Photoshop 7 has gone from sort of works to actually works in the last year.  And I can play Jedi Knight Outcast now too.  So the best thing to do is just try it and see where it is at.  If it isn't working, come back in a few months and try again.

---

### Post by Orfeus on 2007-03-01
OK can somebody tell me what do i have to do clearly please?? I m a bit confused. The game is working fine on the windows partition so it's not the game's problem

---

### Post by steve196 on 2007-03-01
Running stuff in wine is always a gamble although the odds are increasingly in your favour. But your problem seems to have nothing to do with that. Did you doubleclick on setup.exe and get that? If you typed it at a command prompt, afaik you should have used the linux path to the file, not the fake windows one. The \\ stands for a single \ that is read as a letter and not interpreted.

---

### Post by bastiegast on 2007-03-01
Ok wait a minute everyone, this is going a bit offtopic.

To the OP. The problem is very simple, wine can't find setup.exe. Maybe you made a typo?

You ar going to have to provide some details? What exactly are you trying to do? You have a CD which contains the installer? You have setup.exe on your harddisk? Tell us what you typed in the terminal before you got this error.

---


---
title: "Wine!"
date: 2007-01-26
forum: General Help
---

### Post by RyanOmailley on 2007-01-26
I can't seem to get Wine to work for me. I try following the guide, but it gives me some error.

When I type 'wine' into the console I get:

> Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

However my launcher with > wine "C:/Program Files/Macromedia/Dreamweaver 8/dreamweaver.exe" does nothing,

I am very new to this Linux thing, so I'm trying very hard to get stuff to work, haha.

I have tried following this guide [http://www.winehq.com/site/download-deb]("http://www.winehq.com/site/download-deb")
 however I can only get to> apt-get updatebefore it gives me this error: > E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


---

### Post by MrHorus on 2007-01-26
wine is just the command - you have to pass it the path to the windows programme you with to run.

You were almost right but C:\ is a Windows path and means nothing to Linux so what you need to do is mount your Windows drive or install the Windows programme in Linux under wine by running the exe:

```
wine /media/cdrom/setup/install.exe
``` and so forth or in the case of smething installed@

```
wine /mnt/windows/Programe Files/Valve/Half-Life/hl.exe
```

See where I am going with this?

---

### Post by RyanOmailley on 2007-01-26
Not really, but I'll try some things. I want you to understand I have never used linux before, though, and have NO IDEA what I'm doing.

EDIT: Yeah, I have no idea what I'm doing. I think I am making things worse.

---

### Post by RyanOmailley on 2007-01-26
Ok, this is where I'm getting now.
[http://img218.imageshack.us/my.php?image=screenshotsr4.png]("http://img218.imageshack.us/my.php?image=screenshotsr4.png")

---

### Post by mizar001 on 2007-01-26
IMHO using dreamweaver inside wine is dangerous, at least is dangerous starting it from an installed windows instance of this application.

If you want dreamweaver fully functional, you should  re-install it using the wine installer.
With your current DW instance many libraries are not runtime detected by wine, and think that DW access to some windows registry key, but wine can't.

So if you execute DW like you said, you could mess its configuration. 


Think WINE as a windows wrapper, but you must inglobe your windows apps inside a wine environment. Only few programs installed with windows installer work correctly under wine, without reinstall them.

---

### Post by RyanOmailley on 2007-01-26
Wine installer?

I have no idea how to install this then.

---

### Post by RyanOmailley on 2007-01-26
I'm not sure if my wine is messed up, or not configure correctly (how is it supposed to be configured?) but everything I do with it seems to be returning some kind of error. I don't know where I'm supposed to place the things I want to install or how I'm supposed to go about installing them.

Instructions so far have been confusing.

---

### Post by Bloch on 2007-01-26
Dear Ryan;

Wine is not really "consumer level" or beginners software. If someone told you that you can run any windows rogram under wine then they misinformed you. Particularly big complex applications like Dreamweaver are unlikely to run under wine. Multimedia stuff or things that access the internet may also be problematic to run - at the very least you will have to search for .dll files on a windows installation and move them into the system folder of wine.

To satisfy yourself that wine works get a few simple .exe files like notepad.exe hearts.exe and run them from the command line

wine hearts.exe

Then take a look at your hidden .wine directory (you will need to check the "show hidden dircetories box on the file browser). Take a look at you virtual C drive - it's a nomal linux folder in wine .wine/c_drive but wine uses it like a windows C drive.

But really, best of all is to invest your time in finding linux alternatives. If there are none, take a look at the wine website to see if the program you are trying to run is wine-compatible on their database
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by mizar001 on 2007-01-26
> Wine is not really "consumer level" or beginners software. 
Wine is really easy for most windows apps, and it's simple as far you know how windows work.

Dreamweaver is one of the supported programs that runs in wine, even if not all version have been tested. 

RyanOmailley  : If you install your dreamweaver inside wine environnment all should work. After this installation you'll probably can import your projects in the right folder.

> But really, best of all is to invest your time in finding linux alternatives.
Really TRUE, great apps in windows have greater alternatives in Ubuntu.

---


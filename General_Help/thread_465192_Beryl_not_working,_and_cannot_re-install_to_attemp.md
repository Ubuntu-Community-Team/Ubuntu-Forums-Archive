---
title: "Beryl not working, and cannot re-install to attempt to fix."
date: 2007-06-05
forum: General Help
---

### Post by DCGohan on 2007-06-05
Ever since I installed IE6 on Ubuntu I've had random things happen. System hanging, Synaptic manager and add remove load, then close right away. And now Beryl is loaded but not working. Normally I would just try reinstalling Beryl, but that's my other problem.. I can't get to the package manager.  Does anyone have any ideas here?

-edit-
Never mind, Beryl must have crashed, it was switched off from Beryl as the manager. But I still haven't had any luck or help with why Synaptic manager and add/remove doesn't work. I'd appreciate if someone would mind helping. Thanks

ps: I have googled this problem and haven't found anything yet, so I must be using the wrong key words.

---

### Post by dfreer on 2007-06-05
I assume you used the IE4Linux to install IE6 in wine?

---

### Post by DCGohan on 2007-06-06
That would be correct. Also Yet another problem I really REALLY need fixed, anytime I try to uninstall or w/e in the terminal with lets say "sudo apt-get remove azureus" it starts reading the packages, it gets to 70%, this happens "Segmentation fault (core dumped)".
Also I still cannot get add/remove nor synaptic manager to load, it closes almost instanly after I run it.

---

### Post by dfreer on 2007-06-06
wow 0.0 that's not good. 
I don't know if I can help much, but can you install .debs by downloading them manually and double-clicking them?
Try this link to see if you can download, let's say htop or some little program that doesn't need dependencies:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by DCGohan on 2007-06-06
Sorry, I don't get what you want me to try and do. I searched htop, and got to the page, but what am I supposed to download, I don't see any deb files to get.

---

### Post by dfreer on 2007-06-06
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fh%2Fhtop%2Fhtop_0.6.3-1_i386.deb&md5sum=a46c8eac6bac241c4b02cae35f93971c&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fh%2Fhtop%2Fhtop_0.6.3-1_i386.deb&md5sum=a46c8eac6bac241c4b02cae35f93971c&arch=i386&type=main)

Use any one of those servers, and then save the file to your desktop.
Try double-clicking to install the package. 

Also, see if dpkg is broke (dpkg is a part of apt-get, trying to see exactly what is broke on your system) by trying to install the same program from the commandline:
```
sudo dpkg -i ~/Desktop/htop_0.6.3-1_i386.deb
```

---

### Post by DCGohan on 2007-06-06
Double clicking doesn't work, it closes at about 80% done. But in the terminal, i get this

Selecting previously deselected package htop.
(Reading database ... 132977 files and directories currently installed.)
Unpacking htop (from .../Desktop/htop_0.6.3-1_i386.deb) ...
Setting up htop (0.6.3-1) ...

So what does this mean for me?

---

### Post by dfreer on 2007-06-06
It means dpkg works, you should now be able to run:
```
htop
```
It just displays your CPU usage, memory usage, and running processes in the terminal, that's all. But basically this means that dpkg is working ok, or so it seems to be.

NOTE: I really have no idea what is wrong with your system. your best bet would be to hope someone else reads this thread and knows what the problem is, or to reinstall (I think you just have a borked system). Having said that, here's some bandaid solutions if you don't mind trying to tinker with things:
try reinstalling apt:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fapt%2Fapt_0.6.46.4ubuntu10_i386.deb&md5sum=443c5f7f5ca9adce4394de2a035dd7ee&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fapt%2Fapt_0.6.46.4ubuntu10_i386.deb&md5sum=443c5f7f5ca9adce4394de2a035dd7ee&arch=i386&type=main)
```
sudo dpkg --force-depends -P apt
sudo dpkg -i ~/Desktop/apt_0.6.46.4ubuntu10_i386.deb
sudo apt-get update
```
Let us know if you try this, see if the last command works

---

### Post by DCGohan on 2007-06-06
Ok, the top 2 codes worked, but when I did update I got this part way down

83% [22 Packages bzip2 0] [23 Release 15674/34.8kB 45%] [20 Packages 11278/30.2
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages
  Sub-process bzip2 returned an error code (2)

......

shows some packages, then this

Fetched 13.5MB in 32s (420kB/s)
Failed to fetch [http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.bz2](http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Segmentation fault (core dumped)

Synaptic manager still won't work.
I take it that has something to do with it though, those errors?

I know you say I might have to reinstall ubuntu... but I don't want to have to redo EVERYTHING I have done in this last week... I had to fix many bugs, use some bandaids, and mess around for ages to get crap to work with my amd64 and nvidia. Gah, this sucks, if I have to reinstall, I guess I'll just remove my ubuntu partition and go back to good old windows and have errors and freezing out my ***.

Thanks for trying to help me so far though, I hope there's a simple solution to this, and that others read it and understand what my problem is, or ask me to explain more of it.

---

### Post by dfreer on 2007-06-06
Aha! either bzip is corrupted, or the ubuntu.beryl-project repo is down!

Try this:
```
sudo gedit /etc/apt/sources.list
```

put a '#' sign (comment out) any lines that begin like this:
```
deb http://ubuntu.beryl-project.org/
```
so it should look like this:
```
# deb http://ubuntu.beryl-project.org/
```

then try your:
```
sudo apt-get update
```
And post any more errors. if there are no more, try launching add/remove programs or synaptic from the menu, see if those work now.


As for reinstalling, you may not need it now. I just didn't quite know what was wrong with your system before.
However, here's some useful tips in case you ever do have to reinstall:
Keep your /home on a seperate partition. That way you won't lose any important files that you save to your desktop/home folder, and ALL of your preferences, saved information, game info, bookmarks in firefox, etc etc will be saved when you reinstall. Beyond that, you would have to reinstall all of your stuff its true. but if you kept track of what you had to do to fix things it should be pretty quick and painless.
But you probably won't have to reinstall :)

EDIT: If the above codes didn't make sense, post the contents of /etc/apt/sources.list and I'll take a look at it.

---

### Post by DCGohan on 2007-06-06
I still for a Segmentation fault, I don't know if that matters or not, but here's what came up.

dcgohan@dcgohan:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Translation-en_US
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Fetched 7B in 1s (5B/s)
Segmentation fault (core dumped)

And I'll restart then try synaptic manager then post back here if it worked.

-edit-
ok synaptic manager still doesn't work. And if I have to reinstall I'm not even going to bother, I'll stick with windows until I feel like putting ubuntu back on.

---

### Post by dfreer on 2007-06-06
Hmmm. well, you may just have to do that. please realize though that I don't think I've seen this error before, it's not likely to reproduce itself on the next install. but that's your choice whether you want to stay with windows or ubuntu.

---

### Post by DCGohan on 2007-06-06
meh, oh well I'll just leave it as is for now until it totally breaks and i can't do squat. It's not like I can't go on the internet, play doom 3,diablo 2, or other things. Thanks for trying to help out anyway.

---


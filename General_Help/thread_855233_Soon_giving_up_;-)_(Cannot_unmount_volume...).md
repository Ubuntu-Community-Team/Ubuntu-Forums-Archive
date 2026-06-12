---
title: "Soon giving up ;-) (Cannot unmount volume...)"
date: 2008-07-10
forum: General Help
---

### Post by Karlaage on 2008-07-10
Hi.
I've got a problem with installing a game at Wine in Ubuntu 8.04 Hardy Heron. I got the messages "Can not unmount volume" when I press the button to open the CD player. I have tried to find solutions on different forums, but have failed so.

I am fairly new to Linux, but will be happy to fix this problem. Can anyone here help me?

Thank you in advance.

---

### Post by Gunman1982 on 2008-07-10
As long as a program still accesses your cdrom you can not unmount it.

---

### Post by Karlaage on 2008-07-10
Do you think that I must terminate the installation to get opened CD player? Will not it damage the installation of the game?

---

### Post by Gunman1982 on 2008-07-10
Uhm your installation through wine still runs? Or does it ask for the next disc and you just want to change the install discs?

---

### Post by Karlaage on 2008-07-10
It is the one that is the case. The installation is still going, and I am going to insert the CD 2.
Should install the good old C & C Generals ;-)

---

### Post by Gunman1982 on 2008-07-10
Mhh how did you start the installation? from a console or did you just click on the icon on your desktop? I never installed multi-cd stuff with wine but I guess it should unlock the cdrom-drive between disc changes.

---

### Post by Karlaage on 2008-07-10
I right-clicked on setup.exe on CD, and chose "open in Wine". 	
Then started the installation

---

### Post by Karlaage on 2008-07-10
Have to go now, but I'll be back tomorrow. Norwegian time. Thank U Gunman for trying :-)
If any now how, I'll be very happy  :-D

---

### Post by mc4man on 2008-07-10
There are several ways to do this read here [http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)
or do an advanced search in wine forum using wine+cd+eject
Myself I use this from the terminal
```
 wine E:/Setup.exe
``` Where E is the drive letter _that my drive is mapped to in winecfg_ and Setup.exe is _what's on the cd_ (checked by browsing disk.)
Then when it asks for cd2 I just push eject button on drive, insert 2nd disk and click ok in dialog box, ect., just like in windows.
Doing like above resolves the drive locked issue and also makes sure the path for 2nd disk is correct

---

### Post by le singe on 2008-07-12
hello,

I'm having this same problem when trying to install a game through wine - it won't let me eject/unmount the CD when I'm prompted to switch because the CD rom drive is in use.

I tried running the exe through wine by way of the terminal, and still when I try to eject the CD to plop in the next and type:

wine eject d

in the terminal, I get this message:

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Usage: eject [-u] [-a] [-h] [x:]...
    -a  Eject all the CD drives we find
    -h  Display this help message
    -u  Unmount only, don't eject the CD
    x:  Eject drive x:

I'm new to using the terminal... how do I "report usage?"  Must I enter a specific command?

---

### Post by mc4man on 2008-07-13
> in the terminal, I get this message:
preloader: Warning: failed to reserve range 00000000-60000000
That's similar to the error seen with ver. 0.9.59, if you have that ver. installed upgrade to later/latest. Then try again any of the various methods.
If you try the command line i posted just make sure you use the the letter given to your drive in winecfg -> drives and spell the <whatever>.exe right. (browse the install disk to see) Then just use the eject button on the drive itself to go to the next cd like you would in windows.

to upgrade add repo, ect. here (hardy only) or browse releases
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by ad_267 on 2008-07-13
> **le singe said:**
> wine eject d

That should be:
```
wine eject d:
```

---

### Post by Tigera on 2008-12-23
FYI, for people like me who looked through this post for help...
Don't start the setup program from the shell from the same directory.  Otherwise, Ubuntu will list bash as "using" the CD and you won't be able to install.  Example (pretend D is your "Windows" drive letter):

The WRONG way:
```

cd .wine
cd dosdevices
cd d:
wine setup.exe

```

The RIGHT way:
```

cd .wine
wine dosdevices/d\:/setup.exe

```

HTH

---


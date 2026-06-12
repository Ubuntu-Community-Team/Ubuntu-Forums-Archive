---
title: "OMG - this is crazy"
date: 2007-01-14
forum: General Help
---

### Post by hbk41574 on 2007-01-14
Cannot open /media/cdrom0/AOL90S/SETUP90.EXE: No application suitable for automatic installation is available for handling this kind of file.

This is the message i get when i try to install AOL. I get the same message when i try to to install different games that i have on disks. Of course the AOL part of the message is different. What do i need to do so that i can install the programs i have on disks? Please give me detailed info because i am not that bright. 

I am running ubuntu 6.10 , if that will help ya.

---

### Post by 23meg on 2007-01-14
It seems you're trying to install software for Windows on Ubuntu. They won't work natively; however, you may want to try WINE, which is a compatibility layer with which you can get *some* Windows apps running.

---

### Post by GrumpyBob on 2007-01-14
Sounds like you are trying to run Windows installers - you could try Wine or the commercial versions Crossover Office and Cedega ? (there should be information on these support fora if you search). OTOH, I have heard that AOL is not Linux-friendly.

Robert

---

### Post by _simon_ on 2007-01-14
You do know that you don't need the AOL software to connect to AOL?

And as above... EXE is a windows file extension, it MAY work in WINE but I very much doubt you would be able to install AOL software.

As far as games go, some windows games will work via a linux installer, some will work via WINE, some via Cedega but the vast majority will not.

I don't think you've read up on Ubuntu or Linux before installing have you....?

---

### Post by outofnicks on 2007-01-14
Do you *really need* AOL? Everything I've ever heard about it is that it's nothing but headaches, during AND AFTER using the service. Can alternatives be suggested?

---

### Post by Hendrixski on 2007-01-14
Hey.

I see that you are new to Ubuntu.  Welcome to the exciting world of Linux.  It may take you a while to get used to but everyone here will vouch that it is very much worth it.

.exe are windows specific files and they will not work on Macintosh, Linux, Unix, or any other operating system.  They are what is called "proprietary", meaning vendor specific.  In this case the vendor is Microsoft.  if you hear people saying bad things about Microsoft, it is because they use proprietary formats (like .exe for example) to bully the market.

I hope that helps in giving you some background.  As to getting AOL working, is your internet connection working through Linux?  If there is a specific functionality that you are used to in AOL software, then I'm sure you will find another software package that is even better.

---

### Post by gerowen on 2007-01-14
If you're wanting AOL instant messenger, I believe there is a Linux version available on their website, or you can use "Gaim" or "Kopete" depending on which desktop environment you are using.  Since you're using Ubuntu, you are using Gnome, and therefore Gaim would be your best choice.  It comes pre-installed with Ubuntu under "Internet" in the Applications menu.  .exe files, as earlier stated, are files that are proprietary to Microsoft Windows.  Files in that format will not run in any operating system other than Windows.  It is "possible" to run a lot of programs in Linux with a Microsoft compatability layer called "Wine".  To install wine just click "Applications", go to "Accessories" and open the "Terminal".  At the terminal type:
```
sudo apt-get install wine
```
Now that you've made the move to Linux, explore the "Synaptic Package Manager".  It's under "System" and "Administration".  It's a place you can go to find a "ton" of free Linux software to do the things you need to do.  One of the weirdest things you'll do as a new Linux user is get used to the fact that you don't have Microsoft Office, or Microsoft Internet Explorer, or any of the other Microsoft software that you've become accustomed to, and you'll need to find open source alternatives that will run natively in Linux.  Honestly, 9 times out of 10, the Linux software is superior to the Windows software, :-p

Hope this helps!

---

### Post by Sef on 2007-01-14
> What do i need to do so that i can install the programs i have on disks?

What programs are you trying to install?

---

### Post by 23meg on 2007-01-15
[QUOTE=Hendrixski]
.exe are windows specific files and they will not work on Macintosh, Linux, Unix, or any other operating system. They are what is called "proprietary", meaning vendor specific. In this case the vendor is Microsoft. if you hear people saying bad things about Microsoft, it is because they use proprietary formats (like .exe for example) to bully the market.[/QUOTE]Let me nitpick: 

.exe isn't a format per se, it's just the common extension of Windows executable binaries, which also aren't necessarily proprietary; an open source Windows app will have an .exe extension as well. Microsoft isn't the vendor here, since many third parties develop software for Windows, and proprietary doesn't necessarily mean vendor specific; it just means that the software is owned and/or controlled by a proprietor.

---

### Post by peabody on 2007-01-15
> **23meg said:**
> Let me nitpick: 

.exe isn't a format per se

Let me nitpick :).  In a manner of speaking it is. [ [http://en.wikipedia.org/wiki/Portable_Executable](http://en.wikipedia.org/wiki/Portable_Executable) ]  While it's true exe is an extension that could theoretically be applied to any file, it's typically only used on files with a specific format (Microsoft Portable Executable or PE).  It is indeed a documented binary format, albeit one that typically only needs the operating system to work (no external programs required).  Linux and BSD use ELF.  Mac OS X has Mach-O.  Other operating systems have other binary executable formats.

---


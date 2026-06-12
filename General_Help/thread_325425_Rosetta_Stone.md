---
title: "Rosetta Stone"
date: 2006-12-25
forum: General Help
---

### Post by eamonn on 2006-12-25
Hi,

I got one of those "Rosetta Stone" language programs for my laptop. The only problem is the program is only supposed to work on Windows or Mac OSX and I can't seem to figure out how to run it on Ubuntu. Is there any way I could get it to run on Linux?

---

### Post by chipdip on 2006-12-25
Wine. Try to install Wine, I am sure it is in Automatix repositories, so you can try that, once Wine is installed, you can just open up a terminal window and cd to that directory, once in the directory, type "wine programname.exe" without quotes. Sorry if you have some problems understanding any f this, but I am not very good at explaining things.

---

### Post by eamonn on 2006-12-25
How do I install Wine or Automatix for that matter?

---

### Post by KLineD on 2006-12-25
In your computer go to System > Administration > Software Sources. A window opens, Click on Third Party then click on Add. It asks for an apt line. Depending on what Ubuntu version you are:

Edgy
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

Dapper
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Breezy
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main

Click Add Source and it will ask to reload your sources, click ok. When reloading is done you can now go to Applications > Add and Remove and there search for Wine and install it.

There's another way using the console of course, but this is easier.

---

### Post by eamonn on 2006-12-25
Okay, so I got Automatix installed and it said I installed Wine but I can't find Wine on any of my menus? Sorry about the dumb questions. I'm new to this.

---

### Post by KLineD on 2006-12-25
There will be no menus. Go to the directory (from a console) where the .exe for the program you want to install is and there you type 
```
wine myprogram.exe
```
Where myprogram.exe is the name of the program you want to run.

I recommend you try to run first winecfg to configure wine with your drives, etc. Just type winecfg in a console and a window should open.

---

### Post by eamonn on 2006-12-25
I don't even know how to do that. I went into the console and typed "D:\" because it's on a CD and then typed "wine setup.exe" but that didn't work. So what am I doing wrong?

---

### Post by KLineD on 2006-12-25
Ok first of all, in Linux there's no D:\ or C:\ or anything like that. Here everything is treated like a file. For example when you put a CD in, open the console and then type the following:
```
cd /media/cdrom
ls
```

The first command takes you to the directory where your CD is "mounted", that is, when you put the CD in, Ubuntu automatically mounts it to that directory and then you can use the files inside your CD. The second command lists the files inside that directory (equivalent to the dir command in DOS)

Once inside that directory you can type wine setup.exe and hopefully it will work. But I think it's better to try and find an open source replacement for your program, sometimes using wine it's a little tricky and not recommended for a newcomer to Linux.

Check out [http://appdb.winehq.org/appview.php?iVersionId=2497](http://appdb.winehq.org/appview.php?iVersionId=2497) it's the review from WineHQ for the app you are trying to run under Wine.

---

### Post by eamonn on 2006-12-26
I would try an open source version of the program if one were available in Greek but I haven't found one. I got the installer to work, I think, the Rosetta Stone installer went up to 100% and then it closed and stuff started happening in the terminal. It seemed to be going fine until I got this message: 

> 
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)


What is an "InvocationTargetException" and how do I avoid having one?

---

### Post by eamonn on 2006-12-26
Anyone?

---

### Post by FrankVdb on 2006-12-26
Wine works with only a small number of Windows programmes. If the programme was written for Windows, you should run it on Windows. As an alternative for running Windows stuff under Linux, you could install Windows in a virtual machine (e.g. with VMWare) and run Rosetta Stone from there.

---

### Post by artinla on 2006-12-26
It might be necessary to install the windows version of java inside wine.

same method, download the java installer from [www.sun.com/getjava](www.sun.com/getjava) and then in the terminal type "wine javainstallername.exe"

Other than that, I am clueless to why you get that error.

---

### Post by majoridiot on 2006-12-26
> **artinla said:**
> It might be necessary to install the windows version of java inside wine.

same method, download the java installer from [www.sun.com/getjava](www.sun.com/getjava) and then in the terminal type "wine javainstallername.exe"

this is precisely the next step to take...

---

### Post by pissedoffdude on 2006-12-26
you can also go to the exe that you want to launch, right click it and go to open with custom command, and use the command wine

---

### Post by ddumanis on 2006-12-27
Rosetta Stone *online* (not the CD version) works great if you install Crossover Linux from Codeweavers first, then install Firefox for Windows and Shockwave.

---

### Post by OsakaWilson on 2007-02-07
I'm having the same problem. For me the installer goes up to 100% and  then just goes away without any message or anything. 

Rosetta Stone and iTunes are the only two applications keeping me tied to Windows. If anyone knows how to solve this, please help.

---

### Post by cmost on 2007-02-07
Since you aren't an experienced Linux user yet, trying to force 'Rosetta' in Wine may be a bit too grueling.  I suggest you setup a virtualized copy of Windows and run your proprietary software within that.  There are several open source and/or free ways to do this:  1.  VMware Server is now free  2.  QUMU is free and has a nifty K frontend for easy configuration.  It's accelerator module was just recently open sourced.  3.  VirtualDOSbox tools offers a free virtualization environment.  4.  Xen (not easy to setup for a novice.)  5.  KVM is a new virtualization element now a part of Linux kernel 2.6.20 (not easy to setup for a novice.)   6. Parallels Workstation costs under $50.00 USD and offers easy configuration.

Assuming your machine has enough RAM (512 MB is the minimum) you can easily setup a complete Windows 98, 2000, or XP virtual computer that you can access within ubuntu by merely clicking an icon.  From there, you can install any Windows software you want, including Rosetta Stone.  For information on installing some of these virtual machines see here:

VMware:
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)
Note:  for Dapper, but should work on Edgy too

Parallels:
[http://nlindblad.org/2007/01/12/parallels-workstation-in-ubuntu/](http://nlindblad.org/2007/01/12/parallels-workstation-in-ubuntu/)

QEMU
[http://codepoets.co.uk/docs/qemu_windows2000_on_ubuntu_linux_howto](http://codepoets.co.uk/docs/qemu_windows2000_on_ubuntu_linux_howto)
Note:  For Breezy, but should be able to adapt to Edgy or Dapper.

Good Luck!

---

### Post by Choad on 2007-02-07
when i saw the thread title i thought it was going to be about the band "tool"

how disapointing....

---

### Post by Ambimom on 2007-02-07
I doubt that Rosetta Stone can work with Wine.  There is the program itself, but also the language CD-ROM which requires Windows as well. Some things just don't work on Linux......yet.  

In my experience, Wine only works on some things and never on anything as processor intensive as Rosetta Stone.  

It's a sad fact, but unless there is a linux version, or you're willing to dual boot to Windows to use it, you're out of luck.

---

### Post by cmost on 2007-02-07
"It's a sad fact, but unless there is a linux version, or you're willing to dual boot to Windows to use it, you're out of luck."

You do NOT need to dual boot your computer to run Windows software.  See my post above.

---

### Post by Ambimom on 2007-02-07
Rosetta Stone under virtualization would be like swimming in oatmeal even if you could get all the audio video, and record functions to work.....

Virtualization is great...I use it every day, but not everything works 100 percent, especially media, which is what Rosetta Stone relies on.

Linux is the way we should all be going, but you have to be realistic.  Rosetta Stone requires a lot more than either Wine or virtualization can deliver at the moment.

---

### Post by cmost on 2007-02-08
"Rosetta Stone under virtualization would be like swimming in oatmeal even if you could get all the audio video, and record functions to work.....
Virtualization is great...I use it every day, but not everything works 100 percent, especially media, which is what Rosetta Stone relies on.
Linux is the way we should all be going, but you have to be realistic. Rosetta Stone requires a lot more than either Wine or virtualization can deliver at the moment."

Have you actually run Rosetta Stone in a virtual machine?  I concede that if your computer lacks sufficient RAM or CPU horsepower to host an adequate virtual machine than your experience with Rosetta will be less than ideal.  On the other hand, I run Rosetta in a virtualized Windows XP Pro virtual machine, in VMware Workstation 5.5 that utilizes 768 MB of RAM and it works well.  There aren't any "audio, video or record functions" to get going.  It all just works as it would on any standalone XP workstation.  Furthermore, overall performance is equally on par with any standalone XP equipped computer.  That's the beauty of virtualization it's Windows software on Windows - no hacking or fiddling with Wine or other means of non-native emulation required.  From Rosetta's website, the requirements for the software are the following:

# Windows 2000/ME/XP
# Pentium 500 MHz or better processor
# 128 MB RAM
# 100 MB free hard drive space
# 16X CD-ROM drive
# 32-bit color display or better
# 16-bit Windows compatible sound card
# USB Headset Microphone (for voice recognition exercises)

These specifications can be easily virtualized by VMware or Parallels on any modern workstation built within the last four years.  I recommend at least 384 MB of RAM for Windows XP.

I'd say give it a try...what have you got to lose?

---

### Post by frobroj on 2007-02-13
I am running Feisty and just did an apt-get install wine and ran the Rosetta install from disk. Seems to all work fine except audio. I just installed so I will see if I can get it running. If I have any luck I will be sure to post it.

I would also recommend Wines site to see if the software will work or not..
[http://appdb.winehq.org/appview.php?iAppId=1867](http://appdb.winehq.org/appview.php?iAppId=1867)

Just ran winecfg from the command line and set the audio to alsa. Wow this was much easier than I thought it would be. It all works great. Good luck with yours!

Here is where I found the solution
[http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN282](http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN282)

jm

---

### Post by toorima on 2007-02-13
Yeah Rosetta Stone has worked fine with Wine since breezy at least. A little trick for those who doesn't like to use the cd for languages; make a directory and copy all the directory's from the cd into the directory you just created, then in wincfg / Drives you just add a drive, point it to the directory you just made and in show advanced set type to cdrom. I used to have one directory for each language. Hope it's any help.

---

### Post by OsakaWilson on 2007-02-23
After multiple attempts to run Rosetta Stone with wine, I gave up. I haven't heard of anyone successfully doing it. I'm told to try VMware, but I haven't been able to work that one out either. For what it's worth.

---

### Post by ogregore on 2007-02-23
RS runs fine under VMWare Player for me on my Averatec 6240 lappy (although I have 2GB of ram and that may have something to do with it).  I could never get it to properly load under Wine and when I tried to run it inside VirtualBox I would get a "Debugger" error.  

All I did was insert the install CD while running XP in VMPlayer and it installed RS and QuickTime, and on my system it runs just as fast as it runs natively on my wife's XP system, no lag and the sound is in sync.

Cheers
Ogre

---

### Post by xfceslacker on 2007-02-23
> **Ambimom said:**
> Rosetta Stone under virtualization would be like swimming in oatmeal even if you could get all the audio video, and record functions to work.....

Virtualization is great...I use it every day, but not everything works 100 percent, especially media, which is what Rosetta Stone relies on.

Linux is the way we should all be going, but you have to be realistic.  Rosetta Stone requires a lot more than either Wine or virtualization can deliver at the moment.

That is not true. I run Rosetta Stone in a Windows XP VM everyday. Here's my specs:

Processor: 2.4 GHz
RAM: 512 MB

Of course it doesn't go as fast as doing a dual boot, but it is _very_ usable.

---

### Post by erdomi on 2007-03-15
I'm trying to run Rosetta Stone with WINE.  The install seemed to go fine from the Application CD.  But then I put in the language CD and run TheRosettaStone.exe from the .wine file and it doesn't seem to find the language CD.  The program starts up, but then tells me 'no language information found'.  How do I tell it where to look?

Thanks,
erdomi

---

### Post by zorkerz on 2007-03-20
I just installed rosetta stone in WINE and put the language packs on my hardrive as toorima said too.  Thanks for that! Rosetta stone opens fine now and sees the language packs but it does not seem to have any sound.  Kind of an essential part.  In the WINEHQ sombody reported rosetta stone working "almost perfectly"  anyone have any ideas how to get sound to work?

---

### Post by zorkerz on 2007-03-20
Yay! it works with a little help from my friends at the forums and [here]("http://appdb.winehq.org/appview.php?iVersionId=2497") at the app database
heres how i did it:
-created an iso of rosetta stone (v2.0.6.1A for me) and copied the data cd to a folder on my disc (french1 and french2 here)
-installed wine v0.9.32 for feisty with synaptic 
-mounted the rosetta stone cd and installed in wine. note it also automatically installs quicktime
-open winecfg go to the drives tab map both data files as drives and making them cdroms in advanced options
-also in winecfg i checked the alsa, esound, and oss drivers. set hardware acceleration to emulation, default sample rate to 44100 and default bits per sample to 16 (i believe it is the also driver that is actually working) apply all settings
-opened rosetta stone in the applications drop down menu and good to go!

The two snags for me were getting the language data recognized and the audio to work.
good luck to the rest. I have not tried everything but its running just fine so far

---


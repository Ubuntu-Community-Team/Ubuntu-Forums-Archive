---
title: "Questions before installing Wubi"
date: 2008-03-22
forum: General Help
---

### Post by graphicsRat on 2008-03-22
I've just learned about Wubi, and I'd like to try it out. Unfortunately, I've got just one partition on my Windows XP Laptop. Can I still install Wubi? I can't afford to screw up my laptop. I've got all my work on it.

---

### Post by fela on 2008-03-22
the point of wubi is to create a virtual partition and put ubuntu on it, so you don't have to resize the existing windows partition. (if you have one)

but I think that wubi is pretty buggy at the moment, so i don't reccomend it if you can't afford to screw up your laptop, as it could easily (imho anyway)

---

### Post by Powerman2442 on 2008-03-22
Wubi doesn't actually need or even make a new hard disk partition. What it does is it creates a virtual partition installed and managed by Windows. I haven't heard of any Wubi installs messing up hard drive data, although it may be possible. I would suggest backing up any important files on a CD or DVD. 

I am currently using Wubi to run Ubuntu 7.04 Feisty (Which is the only Ubuntu version available, but they have different desktop environments to choose from. Like Gnome, KDE, etc..) My version of of Windows is Vista Home Premium 32-bit. I have had zero problems with Wubi itself. The only thing you should run into is that Ubuntu is extremely different than Windows.

To install it all you have to do is go to wubi-installer.org and download the latest version. Pretty easy to run the setup, editing your log-in information and size of the virtual "partition" that Wubi will install Ubuntu under. A few restarts are needed.

If you ever want to remove Wubi/Ubuntu all you have to do is boot into Windows and go to Add/Remove Programs under the Control Panel and remove Wubi. There you go Ubuntu is removed from your hard drive. If you do uninstall Wubi, the program will save the ISO image that it downloaded (to install Ubuntu), usually in this path. (My) Computer --> C:\ --> wubi-save

If you are not planning on going back to Wubi/Ubuntu after you uninstall it you might want to delete this ISO image as it is upwards of 600 MBs.

Also note that this install could be used without messing around with any real partitions on your hard drive. However, you will never get the full speed of Ubuntu because the OS isn't running on a dedicated partition. Meaning it will run slower. (Slow program load times, etc..) They do have programs to move the entire Wubi install to an actual partition should you choose to later.

Another thing to think about it that you might have a problem with your wireless internet connection or many other driver issues using laptops. If you have a Broadcom internal wireless card I can help you if you need to be connected by a wireless connection.

As with all unknown and fairly large installs I would recommend backing up anything important. Pictures, documents, music, etc.. 

Right now I am in the process of backing up my files to DVD because I am going to attempt to move my Wubi install to an actual partition using LVPM.

---

### Post by fela on 2008-03-23
> **Powerman2442 said:**
> I haven't heard of any Wubi installs messing up hard drive data, although it may be possible.


I know someone that used wubi, and it completely corrupted his HDD (had to reinstall windoze)

---

### Post by ago on 2008-03-23
> **fela said:**
> I know someone that used wubi, and it completely corrupted his HDD (had to reinstall windoze)

Most likely because they hard-rebooted... And hard reboots can corrupt the file system, but that has little to do with wubi... In any case running chkdsk /r from windows/recovery console will often fix things.

---

### Post by waspbr on 2008-03-23
It happened to me in my early days of trying out ubuntu, that is October 2007. I was testing wubi on an old toshiba laptop and at some point the installation froze, so yeah , I ended up having to do a hard reset. I think I ended up having a 22 something error so I had to fix the MBR and then  I ended up having to reinstall windouze.

If you are going to play around with your OSes always back up you essential files and make sure your have recovery.install disks. That is pretty much a given.

However I do think that wubi should be quite safe, it's better to be safe then sorry.

---


---
title: "Failed to start X server [7.04]"
date: 2008-02-14
forum: General Help
---

### Post by David_jcd on 2008-02-14
Hi
I'm completely new to ubuntu and wubi (and pretty new to english language, sorry).
I downloaded wubi 7.04, and started the install. when finished downloading the iso, it prompts to reboot and everything semms to work, until I get an error message:
```
Failed To load the X server (your graphical interface). 
It is likely that it is not set up correctly. 
Would you like to display the X Server output to diagnose the problem?
```
I check [yes] and it shows me a lot of stuff which i don't understand:confused:, I check [ok] and it asks me if I want to have an even more detailed description of the problem. After viewing it,, i click [ok] again and the install progress seems to go on, but it hangs up while
```
running local boot scripts (/etc./rc/local)
```
I don't know what to do, can anybody help me?
I have a Dell inspiron 1520 laptop with GeForce Go 8600M GT.

Thanks!!!

---

### Post by erginemr on 2008-02-14
I would say forget about wubi 7.04 and download and install from the Ubuntu Gutsy Gibbon live CD. There should even be a customized DELL version of Gutsy Gibbon installer CD somewhere on the net, which should address most of the problems that DELL users experience while using Ubuntu.

---

### Post by erginemr on 2008-02-14
Here is the link for DELL remastered Live **DVD**:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

And here is the link for stock Ubuntu Live/Installer CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by David_jcd on 2008-02-14
> **erginemr said:**
> Here is the link for DELL remastered Live **DVD**:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

And here is the link for stock Ubuntu Live/Installer CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Impressed. I'll try installing it, even i i can't find the right version for my own laptop... Anyway, i think I'll keep on trying with wuby, cause I only have a windows partition, and it isn't completely safe to uso Gparted to resize it. As soon i'll format the pc, i'll make a dedicatet linux partition.
Thank you very much!

---

### Post by erginemr on 2008-02-14
> **David_jcd said:**
> Impressed. I'll try installing it with wubi.
Thank you very much!

It is your call, but be advised that Gutsy Gibbon (7.10) is a later version than Feisty Fawn (7.04), which has the latest versions of the installed Linux software and supposedly should support more hardware. 

I think you are worrying about partitioning your hard drive, but if you are determined to use Linux, sooner or later, you will need to install it. The only thing to be wary about is to degragment your Windows drive first, and to be careful not to wipe your Windows drive when asked by the installer.

Besides, these Live CD's (or DVD's for that matter) will ensure you whether your hardware works without touching anything on your system.

---

### Post by David_jcd on 2008-02-14
> **erginemr said:**
> 
I think you are worrying about partitioning your hard drive
Thet's it! I was editing my post while you were writing yours!

I'm not so determined to use linux, and that's why i want to have a look at it using wubi, which, I think, is much better than a live cd...

---

### Post by erginemr on 2008-02-14
Understood. Then we should concentrate on your problem. I will try to find whatever I can on wubi and come back to you. I hope your thread will attract the attention of other forum users too.

---

### Post by erginemr on 2008-02-14
I have downloaded an alternate installer CD and went through the installation of a text-only system on a virtual hard drive by using VirtualBox. From what I saw, I believe the installer cannot detect the graphics card on your system correctly and moves on with the install successfully and when it comes to the stage "running local boot scripts", it just finishes its job and stops with no indication on what to do.

It took a few "Enter" strokes from the keyboard to get a prompt for my user name / password login. So, first check whether your system really freezed or if you can get a login prompt by pressing "Enter" several times.

If you can login and reach the text mode screen, login first with your user name and password and try to configure your "/etc/X11/xorg.conf" file with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And try to start your X server with these settings:
```
startx
```
or
```
sudo /etc/init.d/gdm start
```

---

### Post by David_jcd on 2008-02-14
hi!
First of all, _**thank you so much**_ for helping me!!!
I tried to do what you said. I came to the log in and tried to reconfigure the xorg.conf, checking the resolution I use with windows (1280x800) and unchecked the others.
Then I tried the Startx command, but an error message appeard, saying:
[EE] No display devices found
[EE] Screen(s) found, but not have a usable configuration
or something like that.
So I tried writing
sudo /etc/init.d/gdm start
and gnome seemed do start: 
```
Starting GNOME Display Manager   [ OK]
david@ubuntu ecc...
```
At this point I didn't know what to do and rebooted, but after reboot I couldn't log in any more. As the
"running local boot scripts" appeared, i pressed Enter a lot of times, but nothing happened!

---

### Post by erginemr on 2008-02-14
Aarrgh! It is very difficult to help you on a troublesome installation, Without a working networked environment, even if I said post the contents of your /etc/X11/xorg.conf file, it would be next to impossible for you to do that.

Things would be much easier if you had downloaded an Ubuntu Live CD and booted from there. No no, it won't work, beause wubi installs to a virtual file system, which really is one big, huge file. There are free Windows ext2 viewers but they won't work either due to the very same reason.

So really, I would say ditch wubi and all files (and your virtual Ubuntu system) installed with it, download a Live CD and try if you will like Ubuntu or not from there. You don't have to install anything for now, just put the CD in the drive and boot. Don't worry, your existing system will be kept intact.

Otherwise, if you want to strive more with the current installation, I would suggest pressing Esc during the booting phase of Ubuntu and select "Recovery Mode" (second one I believe) from the Grub menu. Then, you should have your text-mode environment back. Then, once you have the prompt back, copy xorg.conf file to a diskette (if you have a 21/4" diskette slot, which is unlikely) or USB drive (mounting them would be easier said than done, by the way). Post here and let us talk more. 

But anyway, as I said it is not worth the effort. Ditch it and grab a Live CD.

---

### Post by erginemr on 2008-02-14
Alternatively, you can install VirtualBox in Windows, a free Virtual PC software, as I did above:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

and emulate an Ubuntu installation on a virtual drive. Give it a go, it is really easy, and fun this way. You can use the Alternative Ubuntu 7.04 CD that wubi has downloaded from the web to feed to VirtualBox (that is, to load it as a virtual CD image). It should be somewhere in your existing wubi installation.

---

### Post by David_jcd on 2008-02-14
> **erginemr said:**
> 
But anyway, as I said it is not worth the effort. Ditch it and grab a Live CD.
Ok. I'm going to uninstall wubi and download the ubuntu 7.10 live cd/dvd.
And maybe il'' learn to use gparted and create a new partition for ubuntu. I thought it would be useful to have three partitions, if possible. The first one for vista, the second one for ubuntu, and the third one would be a shared partition, for documents, music, pictures... to be used
with both OSs. What filesystem should I set in this documents partition?
Thank you very much again!

edit:
> Alternatively, you can install VirtualBox in Windows, a free Virtual PC software, as I did above:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

and emulate an Ubuntu installation on a virtual drive. Give it a go, it is really easy, and fun this way. You can use the Alternative Ubuntu 7.04 CD that wubi has downloaded from the web to feed to VirtualBox (that is, to load it as a virtual CD image). It should be somewhere in your existing wubi installation.
That's a good idea! I can use virtualbox as an alternative tu wubi, to test ubuntu before definetively install it.

---

### Post by syn4k on 2008-02-14
Yeah, I have this same issue. And nope, NOTHING solves it that I've tried. The ABSOLUTE ONLY thing I have not tried is this so called "DELL" alternative CD. I really think this is pretty lame. It's too bad this software isn't written better pft.

UPDATE: lol this is lame...there isn't an alternate CD for the DELL Latitude D630 that I can find...I'm starting to think that Ubuntu is just not for me. After three months of trying to fix this and about 80 hours of research. I'm fricken tired of this noobish crap.

---

### Post by erginemr on 2008-02-15
> **David_jcd said:**
> Ok. I'm going to uninstall wubi and download the ubuntu 7.10 live cd/dvd.
And maybe il'' learn to use gparted and create a new partition for ubuntu. I thought it would be useful to have three partitions, if possible. The first one for vista, the second one for ubuntu, and the third one would be a shared partition, for documents, music, pictures... to be used
with both OSs. What filesystem should I set in this documents partition?
Thank you very much again!
...

You are welcome. Just be careful, when you have decided to do the real installation, not to wipe off your complete Vista partition by mistake. The following wiki is a good read that explains the steps of installation graphically:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I am also dual-booting Ubuntu with Windows (XP) and have a third partition in NTFS for shared documents. You can do the same. Ubuntu 7.10 is capable of reading from and writing to NTFS drives safely, thanks to a driver called NTFS-3G.

Take care & Have fun with Ubuntu!

---

### Post by David_jcd on 2008-02-15
> **erginemr said:**
> You are welcome. Just be careful, when you have decided to do the real installation, not to wipe off your complete Vista partition by mistake. The following wiki is a good read that explains the steps of installation graphically:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I am also dual-booting Ubuntu with Windows (XP) and have a third partition in NTFS for shared documents. You can do the same. Ubuntu 7.10 is capable of reading from and writing to NTFS drives safely, thanks to a driver called NTFS-3G.

Take care & Have fun with Ubuntu!
perfect! I'm saving the walkthrough for when i'll need it. I didn't know ubuntu coul read and write to Ntfs...
bye, hope you have a good weekend!

---


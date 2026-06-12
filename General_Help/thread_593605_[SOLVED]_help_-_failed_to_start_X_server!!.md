---
title: "[SOLVED] help - failed to start X server!!"
date: 2007-10-27
forum: General Help
---

### Post by timofthec on 2007-10-27
guys, Ive recently upgraded by PC and now when I try to boot to ubuntu it seems to load as normal and then GUI does not appear and I am faced with a blue screen and a white box that reads: -

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

The options after hat are simply yes or no.  selecting yes gives me this message: -

"The X server is now disabled.  Restart GDM when it is configured correctly."

selecting "ok" takes me to a promt "xxx-desktop login: ".  logging in takes me to the prompt "xx@xx-desktop:~$"  and I have no idea what to do from here.

The changes to my pc were a new motherboard,Dual Core Processor + a new nvidia geforce card where a before I was using an ati card (I assume that this is the problem)

I've had a look round the forums and have tried to load ubuntu through recovery mode and then tried the command "dpkg-reconfigure xserver-xorg."  This presented me with a lot of options that I had no idea what to do with and just took the default options presented.   However, this has had no affect and I cannot load the os.

Any ideas anybody?  Please be aware that I am a total noob with linux so if there is a fix for this it will have to be presented to me in noddy fashion :)

---

### Post by PmDematagoda on 2007-10-27
Do:- 

```
sudo dpkg-reconfigure xserver-xorg
```

and select the Nvidia driver in favour of the ATi one.

---

### Post by Ricardo_V on 2007-10-27
when you run dpkg-reconfigure xserver-xorg, are you choosing VESA drivers? Or do you choose your graphics card driver? Maybe you should first try using VESA drivers and check if your desktop loads. If it goes well, try downloading specific drivers from nvidia.

---

### Post by timofthec on 2007-10-27
thx for the quick responseguys.

> **PmDematagoda said:**
> Do:- 

```
sudo dpkg-reconfigure xserver-xorg
```

and select the Nvidia driver in favour of the ATi one.

PmDemat - tried it again using sudo.  I can see no option for nvidia as such so I selecetd "nv".  Went through all of the optins again and restarted but am still getting the same error.

Ricardo - yeah, ive tried it by slecting the "vesa" option but that didnt work either.

:(

---

### Post by PmDematagoda on 2007-10-27
Ok, try this:-

1) Download the latest Nvidia driver for Linux from the website. The installation instructions are given there as well.

2) You may install the drivers through Recovery Mode or by killing the X-server, but I'm not sure about killing X-server and Recovery Mode is more reliable.

3) Then reconfigure the X-server using:-

```
sudo dpkg-reconfigure xserver-xorg
```

Then try to see if the GUI works properly.

---

### Post by timofthec on 2007-10-27
> **PmDematagoda said:**
> Ok, try this:-

1) Download the latest Nvidia driver for Linux from the website. The installation instructions are given there as well.

2) You may install the drivers through Recovery Mode or by killing the X-server, but I'm not sure about killing X-server and Recovery Mode is more reliable.

3) Then reconfigure the X-server using:-

```
sudo dpkg-reconfigure xserver-xorg
```

Then try to see if the GUI works properly.

Thnx for that PmDemata, and heres where my complete lack of understanding kicks ins.  I can boot the pc to xp and get to the nvidia website to download the driver, however, I am not able to download it to the ubuntu partition cus ntfs does not recognise it. I've no idea how to use the comand line interface in ubuntu :(

---

### Post by PmDematagoda on 2007-10-27
And here's where the terminal is your ally. 

First get :-

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)
 
and install it, it gives support for ext2 and ext3 drives. Just don't over use it.

Then copy the downloaded the file to /root/Desktop

Then go through Recovery Mode and install the driver as given on the web site.

Then just do:-
```

sudo dpkg-reconfigure xserver-xorg
```

and select the Nvidia driver, you may keep the other default choices. After reconfiguration do:-

```
startx
```

to see if X-server works properly.

---

### Post by timofthec on 2007-10-27
> **PmDematagoda said:**
> And here's where the terminal is your ally. 

First get :-

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)
 
and install it, it gives support for ext2 and ext3 drives. Just don't over use it.

Then copy the downloaded the file to /root/Desktop

Then go through Recovery Mode and install the driver as given on the web site.

Then just do:-
```

sudo dpkg-reconfigure xserver-xorg
```

and select the Nvidia driver, you may keep the other default choices. After reconfiguration do:-

```
startx
```

to see if X-server works properly.

damn it p Ext IFS will not work!!!

I downloaded and installed it as directed but wen I try to access the linux drive in xp I get told that it needs formatting.  Dwnloaded and ran Mountdiag.exe and that tells me that the file system has transactions left in the journal and that a driver cannot access it to prevent data loss.  It tells me mont the EXT3 on linux to try and solve the problem (what ever that means)!!!

erm - help

---

### Post by timofthec on 2007-10-27
as an update, the exact wording I get wen I run mountdiag is: -

The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.10 software did not mount it beause there is at least one incompat feature flag set.  The Ext2 IFS software does not implement:
* needs_recovery *
Here we have an Ext3 file system which has transactions left in its journal.  A pure Ext2 driver must not access such a volume which is in that state <to prevent data loss!>.
You may solve it by mounting it on Linux <which has a kernal with Ext3 support>.  Be sure that you cleanly dismount it, before you shutdown Linux.  After hat the Ext2 IFS software should be able to access the volume.

Any ideas or am I looking at re-installing ubuntu.  I'd rather not do that if at all possible because setting up the wireless conection is a real pain :(

---

### Post by timofthec on 2007-10-27
first off, ignore the earlier problem with ExtIFS, I managed to sort that out by running recovery mode again and then using the command "shutdown -r now".  That seems to have closed all of the open processes :)

I'm therefore ready to do this bit: -

> **PmDematagoda said:**
> 

Then copy the downloaded the file to /root/Desktop



I can now get access to the Linux drive through XP and there is a root directory, however, I cannot see a "Desktop" sub directory.  is "/root/Desktop" the correct path?  I have found a "Desktop" directory but it is in "/home/xxxx/" is that the correct place to put the nvidia drivers?

---

### Post by timofthec on 2007-10-27
ok, i copied the nvidia drivers to both locations and run recovery.  At the command promt I ran

 sh NVIDIA-Linux-x86-100.14.11-pkg#.run

but all I get is a message that "Can't open sh NVIDIA-Linux-x86-100.14.11-pkg#.run"

help plz

---

### Post by timofthec on 2007-10-27
still not got a resolution to this problem - any help greatly appreciated

---

### Post by PmDematagoda on 2007-10-27
Did you try with different methods, such as without .run or by first making it an executable?

---

### Post by timofthec on 2007-10-28
> **PmDematagoda said:**
> Did you try with different methods, such as without .run or by first making it an executable?

ok, tried running it without .run on the end and also from both the desktop prompt as well as the root prompt and no luck so far.   The Nvidia directions just say to go to the download location and then type "sh NVIDIA-Linux.... etc".  

I have no idea how to make the file executable from the command prompt and would that even work?

Anyhows, still looking for any help to solve this issue please guys

---

### Post by PmDematagoda on 2007-10-28
Make the file executable using:-

```
sudo chmod +x nameoffile
```

and then try the sh command.

---

### Post by timofthec on 2007-10-28
right,this is getting frustrating now.

PmDemat - I tried "sudo chmod +x NVIDIA-Linux-x86.100.14.11-pkg1.run" and get the message "chmon: cannot access 'NVIDIA-Linux-x86.100.14.11-pkg1.run': No such file or directory".

I am running the command from root@xxx-desktop:~#.  Typing "ls" shows that the file is there :confused:

Is it possible to fix this problem or should I just reinstall ubuntu over the current instalation?  If I do reinstall, is thre an option to repair the installation or am I looking at reformatting the partition and do a full install?

---

### Post by timofthec on 2007-10-28
any one?

---

### Post by PmDematagoda on 2007-10-28
Ok, what do you see when you type

```
ls
```

?

---

### Post by timofthec on 2007-10-28
when I type "ls" at "root@xxxx-desktop:~#" it simply shows the file "NVIDIA-Linux-x86.100.14.11-pkg1.run"

---

### Post by timofthec on 2007-10-28
> **timofthec said:**
> Is it possible to fix this problem or should I just reinstall ubuntu over the current instalation?  If I do reinstall, is thre an option to repair the installation or am I looking at reformatting the partition and do a full install?

This seems a bit beyond me, so, anyone have an answer to my other question?

---

### Post by timofthec on 2007-10-28
anybody?

---

### Post by timofthec on 2007-10-28
ok, I can get access to the ubuntu partition via xp - can I format the partition through xp?

---

### Post by timofthec on 2007-10-29
anybody?

---

### Post by timofthec on 2007-10-29
For anybody else who is having the same problem with this as me, I have managed to find an answer from another forum.  I was told to boot to recovery, type "

> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken

and reboot.  Computer booted straght into the normal ubuntu logging in screen :)

PmDematagoda - thanx for all your help and patience with this, I appreciate the effort :KS

All I need to do now is work out how to put "solved" in the thread title - minor issues :)

---


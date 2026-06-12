---
title: "Failed to start..."
date: 2007-06-30
forum: General Help
---

### Post by dwhit26 on 2007-06-30
I don't know if this problem has come up before but...

I just installed UBuntu Desktop 7.04 onto my computer. The live CD started up fine, and I installed via there. The install went fine and smooth, no errors or problems. It reboots and I get this page saying:
> 
Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes>    <No>

I select yes and it gives me this:
> 
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0 Release 7.2
Build Operating System: Linux UBuntu Linux
Current Operating System: Linux UBuntuLinux 2.60.20-15-generic #2 SMP
Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
[INDENT]Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version.[/INDENT]
Module Loader Present
Markers: (--) probed, (**) from config file. (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.o.log", Time: Sat Jun 3 20:37:27 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.
Fatal server error:
no screens found
<Ok>


I select <Ok> and it asks me:
Would you like to view the detailed X server output as well?
S I select <Yes> and it gives me a long list of things that I would rather not type all out but if it would help some let me know I can type it all out. But I select the <Ok> and it tells me:
The X server is now disabled. Restart GDM when it is configured correctly.
I select <Ok> and it brings me to a screen that tells me to login. I try to log in with "root" and the password I made earlier "Password01".
Am I doing something incorrect or am I just too noobied for Linux to know what I am doing? :(


>>EDIT: I just wanted to add I am dual monitoring.. When I was using it off of the live CD it did some garbled up stuff on my primary monitor but the other one displayed fine. Maybe this is part of the problem? I also have an onboard video card that I have disabled in my motherboard BIOS.

---

### Post by GeeZor on 2007-06-30
can you or can you not logon to your system as root? if you can, and you have network you should download the NVIDIA - linux  driver from the nvidia website while using the CD.
then when logged on as rood, run that file  (after making it executable with chmod 777) 
You do need the header and source files of the kernel you are running to let the installer compile your driver module. 
or you could upgrade to feisty throught apt-get and after that use the nvidia driver that is available from the Ubuntu Feisty repositry  ( sudo apt-cache search nvidia  ) 
i think it was nvidia-glx but not to sure.. you should check that yourself

but basically, your problem is that you do not have the kernel module (driver) installed on your system and need to fix this manually as described above.

PS. upgrading is done using the following command:
apt-get dist-upgrade    (as root ofcourse)

---

### Post by dwhit26 on 2007-06-30
I Cannot log in as root. If I put in the CD i can select for it to boot into the live cd version.

---

### Post by GeeZor on 2007-06-30
if this is a fres installed system try this.
```

sudo passwd root

```
you will be asked to enter a password. That is the password that belongs to the user you used to loging. After that you will be asked a password. That will password will become the root password. verify that and your done.
now type
```

su -

```
enter the root password.

---

### Post by Crafty Kisses on 2007-07-01
> **dwhit26 said:**
> I don't know if this problem has come up before but...

I just installed UBuntu Desktop 7.04 onto my computer. The live CD started up fine, and I installed via there. The install went fine and smooth, no errors or problems. It reboots and I get this page saying:

I select yes and it gives me this:


I select <Ok> and it asks me:
Would you like to view the detailed X server output as well?
S I select <Yes> and it gives me a long list of things that I would rather not type all out but if it would help some let me know I can type it all out. But I select the <Ok> and it tells me:
The X server is now disabled. Restart GDM when it is configured correctly.
I select <Ok> and it brings me to a screen that tells me to login. I try to log in with "root" and the password I made earlier "Password01".
Am I doing something incorrect or am I just too noobied for Linux to know what I am doing? :(


>>EDIT: I just wanted to add I am dual monitoring.. When I was using it off of the live CD it did some garbled up stuff on my primary monitor but the other one displayed fine. Maybe this is part of the problem? I also have an onboard video card that I have disabled in my motherboard BIOS.

You should try reconfiguring your X server, try this command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by GeeZor on 2007-07-02
```
sudo dpkg-reconfigure xserver-xorg
``` will not do the trick unless you install the nvidia dirver.


```
sudo apt-get install nvidia-glx
``` should help you out.
Note that you should also install the suggested packages...

to find nvidia packages maching your kernel:
```
sudo apt-cache search nvidia
```

good luck although you shouldn't need it.

---


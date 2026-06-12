---
title: "How do I move/ install windows into Ubuntu"
date: 2007-11-30
forum: General Help
---

### Post by MR.UNOWEN on 2007-11-30
Hello,

I was wondering how you run and install windows over Ubuntu and take windows files from a preexisting windows partition and move it over to Ubuntu?

---

### Post by PmDematagoda on 2007-11-30
Could you please be a little clearer?

You want to install Windows over Ubuntu yet you want to transfer files from a previous Windows installation to Ubuntu? I'm sorry but I do not get it.:confused:

---

### Post by MR.UNOWEN on 2007-11-30
I thought you had to install a new version then transfer files from a preexisting version. So I can just transfer the whole file system over?

So how do I do it?

---

### Post by PmDematagoda on 2007-11-30
You could try upgrading your Ubuntu OS to Ubuntu 7.10, but **first back-up all you important files and data before you do that**. If the upgrade works properly then it would make things very much easier.

---

### Post by MR.UNOWEN on 2007-11-30
Well I'm going to install gutsy on separate hard drive. I was thinking of taking windows xp from the prior hard drive and then turn that one into storage, if the transfer goes well. I basically want xp to run over the Ubuntu file system

---

### Post by PmDematagoda on 2007-11-30
Yes that can work, just make sure that at the Partitioning part of the Ubuntu installation you select the proper drive, not the storage drive, otherwise you might lose all your data.

---

### Post by MR.UNOWEN on 2007-11-30
I know how to install Ubuntu, what I want to know is how do I get XP running over Ubuntu such that on my Ubuntu desktop I have windows running in a window just like those screen shots in the gallery..

[IMG]http://ubuntuforums.org/g/images/388856/large/1_linuxwinxp.png[/IMG]

---

### Post by rechick on 2007-11-30
You will need to run a virtual machine (Virtualbox or vmware  both free) and install WIndows in that machine. If you run VMWare there is a tool which will convert the existing real machine into a virtual machine. This virtual machine can then be accessed from the VMWAre server running under linux. Be warned, because this will change parameters in the perceived hardware configuration the windows installation may consider this a new computer and require reactivation.

---

### Post by MR.UNOWEN on 2007-11-30
Which of those two allow xp to go to full screen and not just a frame? Also will it transfer the files over, or do I have to copy them over into a folder? Also what about drivers, will I need any?

---

### Post by sirdilznik on 2007-11-30
I'm not sure if there is anything specific in the kernel that needs to be done for vmware, because I've never tried it, but as far as accessing the filesystems, I believe the generic kernel will already have support for both the ntfs and fat filesystems.

---

### Post by timcredible on 2007-11-30
the process is you install virtualbox or vmware, then you run that program and choose to install a new virtual machine, and it'll ask you to insert the windows CD, it runs the installer, and after that's done, you  have a complete installation of windows running within the virtual machine software.  i don't think you need any drivers for graphics or keyboards or anything like that because the virtual machine takes care of that.  you then reinstall any programs you want.  as for transferring your data files, don't know the easiest way to do that.  you'll want at least 1gb of memory to run it since you're running 2 operating systems at the same time.

---

### Post by forestpixie on 2007-11-30
IF you use virtualbox - when you've got the virtual machine installed and working you need to install the guest additions, it's in the devices menu, once that's in - you get the mouse working properly between the virtual machine and your buntu installation, also you get seamless mode - which is what you're referring to 

Absolutely no idea if you can do the same with vmware, which is the virtual that has the tool to let you use an existing win install.

Probably not the answer you're looking for, but hope it helps some

---

### Post by MR.UNOWEN on 2007-11-30
Can VIrtualBox go full screen, such that there's no window frame.

---

### Post by forestpixie on 2007-11-30
Yes - 2 screenshots - 1 filling the screen, once you've got the guest additions you can do that, other scrnsht - virtual machine started and then set seamless so it can be in the same desktop as you're linux apps.

---

### Post by Craigus on 2007-11-30
They can both do full screen modes, although I don't think VMWare Player can do the seamless trick.

It is also possible to run your existing XP installation in a virtual machine. Here's a guide to do this with XP and VMWare Player:

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")

You will have to set up a second hardware profile in XP (explained in the tutorial)  and you may have to reactivate, depending on your XP version.

---

### Post by fjgaude on 2007-11-30
> **MR.UNOWEN said:**
> Which of those two allow xp to go to full screen and not just a frame? Also will it transfer the files over, or do I have to copy them over into a folder? Also what about drivers, will I need any?

In Unbutu you can have many desktops. Notice in my screen shot I have five, with VMware running in the fourth. You can size the windows to see both Linux and WinXP at the same time. When you move to another desktop, it's all Ubuntu. Or you can run WinXP full screen. Lots of flexibility.

   1. Download the vmware server from vmware website, vmware.com.
   2. Install linux headers matching your kernel version, xinetd and build-essential (likely already on your computer)
   3. unpack the software
   4. run sudo ./vmware-install.pl
   5. follow the guide, then
   6. gksudo gedit /etc/init.d/mountdevsubfs.sh
   7. uncomment 42-45 lines #mkdir -p /dev/bus/usb/.usbfs

To uninstall sudo ./vmware-server-distrib/bin/vmware-uninstall.pl

Let us know if you need more info.

---

### Post by MR.UNOWEN on 2007-12-01
It's not working,

Once I click finish isn't it supposed to go to load the xp disk?

---

### Post by forestpixie on 2007-12-01
you need to add yourself to the vboxusers group in system >admin > users and groups and the first scrnsht tells you what it wants you to do. DIdi you install vbox from the repo or from the download?

---

### Post by MR.UNOWEN on 2007-12-01
Thanks

---

### Post by forestpixie on 2007-12-01
hi - glad everything's nearly right :)

if you're talking about the panels at top, bottom etc - right click > properties in general tab you can put hide buttons or do the autohide thing

hope that's what you mean

---

### Post by MR.UNOWEN on 2007-12-01
Thanks

The only issue I'm having is now my audio is suddenly unable to go above a certain level and the quality isn't that good.
Also how do I get it to see my local file system

---

### Post by fjgaude on 2007-12-02
You have to do it through Shared Files... set that up in Ubuntu, then you use Network connections in Windows down at the bottom of Windows Explorer.

Lots to learn to all this cutting edge stuff working, eh?

---


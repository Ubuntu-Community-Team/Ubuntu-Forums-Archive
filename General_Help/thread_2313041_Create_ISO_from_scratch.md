---
title: "Create ISO from scratch"
date: 2016-02-09
forum: General Help
---

### Post by jimmyh1972 on 2016-02-09
Hi - I'm trying to create a new version of Ubuntu using this wiki - [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
when I run the command - sudo mount --bind /dev chroot/dev
It gives this error - mount: mount point chroot/dev does not exist
What is wrong? how can I continue?
Thank's

---

### Post by tokyobadger on 2016-02-09
I think the code should be
```
sudo mount --bind /dev chroot /dev
```
note the space between chroot and /dev; I'm surprised that /bin/bash is not called in that code but I may be mistaken

---

### Post by jimmyh1972 on 2016-02-09
i tried - sudo mount --bind /dev chroot /dev
It gives this error
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by tokyobadger on 2016-02-09
maybe [this tutorial is more up-to-date/accurate](https://www.safaribooksonline.com/library/view/ubuntu-hacks/0596527209/ch01s04.html) - the steps to chroot look more familiar to me

---

### Post by deadflowr on 2016-02-09
Did you leave the working directory that chroot is in?

The commands have nothing to do with chrooting, but binding the mount points in the user-created chroot sub-directory.
If need be, you can try mounting to the full path.
Example, if I made a chroot directory in my Documents folder, I might run
```
sudo mount --bind /dev /home/me/Documents/chroot/dev
```
But the full path shouldn't be needed if you stayed in the working directory that you where in when you created the chroot directory.

My 2 cents

Edit: did the debootstrap command run properly?

---

### Post by jimmyh1972 on 2016-04-17
Hi 
My name is Jimmi (20 years in IT & development {Java,Bash,Python})
I have a task to create a customized ISO from the Ubuntu distro - never done it before
I know it can be done with mounting the ISO into a chroot do your changes & then recompile it as a new ISO
Do you have a good detailed step by step wiki for that?
Thank's ahead

---

### Post by ian-weisser on 2016-04-17
A custom install can be created several ways:
[preseed file]("https://help.ubuntu.com/lts/installation-guide/armhf/apbs02.html")
[OEM installer ]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview")
[Manually]("https://help.ubuntu.com/community/LiveCDCustomization") (step by step)
Post-install script

Other projects, like Debian Live and Ubuntu Customization Kit, also exist in various stages of dormancy.

How customized do you want it? Merely a few different packages? Whole different (unsupported, unpackaged) stack of something? Different versions or different software sources? Totally different artwork and branding? Built-in admin account with ssh key?

---

### Post by jimmyh1972 on 2016-04-19
Hey Ian
I would like to customize the whole system adding my scripts and progs (bash, python, java) , customize the desktop and make an ISO.
it's not for published distro it's private for my IT team.
I don't want to use any GUI customization tool prefer terminal (and hard work...)
I know it can be done with squashfs but never done it before...
i would be very happy to get/redirected to a A-Z tutorial
Thank's ahead - Jimmi

---

### Post by sudodus on 2016-04-19
> **jimmyh1972 said:**
> Hey Ian
I would like to customize the whole system adding my scripts and progs (bash, python, java) , customize the desktop and make an ISO.
it's not for published distro it's private for my IT team.
I don't want to use any GUI customization tool prefer terminal (and hard work...)
I know it can be done with squashfs but never done it before...
i would be very happy to get/redirected to a A-Z tutorial
Thank's ahead - Jimmi

I think the easiest way for an 'in house' system would be to make an OEM system and when you are happy with it, you can install it manually (***rsync***, ***grub-install*** etc) or via the [One Button Installer](https://help.ubuntu.com/community/OBI) or by cloning with [Clonezilla](clonezilla.org/).

Otherwise, there are the links by *ian-weisser*, and a lot of hard work. Don't expect to get help with all the details, but at the end you will be able to create your own re-spin or even your own linux distro.

In addition there is also ***Remastersys***, that you might be able to get if you are prepared to pay for it from the original developer, *fragadelic*. (I don't know if it is still developed and how it works with new versions of Ubuntu.)

You can find a fork via the following link [http://www.remastersys.org/](http://www.remastersys.org/). I don't know how well it works, maybe worth trying. A fresh version was uploaded to github during this month. See this link: [**[https://github.com/ch1x0r/LinuxRespin](https://github.com/ch1x0r/LinuxRespin)**](https://github.com/ch1x0r/LinuxRespin)

Please keep us informed! I think many users at the Ubuntu Forums would like to know how things work for you. Good luck :-)

---

### Post by Bucky Ball on 2016-04-19
*Thread moved to **General Help**.*

---


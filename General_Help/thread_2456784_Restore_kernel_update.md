---
title: "Restore kernel update"
date: 2021-01-19
forum: General Help
---

### Post by katyperry78 on 2021-01-19
Hello, 

I have some trouble because of a kernel update. I am using Ubuntu 16.04 (dualboot with windows 10) because I need ROS Kinetic, on my Lenovo Thinkpad P51. ROS is my only Ubuntu experience. I want to control a Franka Emika Panda robot, therefore I need a real-time kernel. I tried following their guide: 
[https://frankaemika.github.io/docs/installation_linux.html](https://frankaemika.github.io/docs/installation_linux.html)

I had a 4.15 kernel, which did not have a real-time possibility according to the guide. The guide refered to: 
[https://mirrors.edge.kernel.org/pub/linux/kernel/projects/rt/](https://mirrors.edge.kernel.org/pub/linux/kernel/projects/rt/)
Therefore I followed the Setting up real-time kernel part (in the guide) to install kernel 4.16. I was able to follow the guide up until 
fakeroot make -j4 deb-pkgTHis command worked. The next one: 
sudo dpkg -i ../linux-headers-4.14.12-rt10_*.deb ../linux-image-4.14.12-rt10_*.debdid not work. I could not find the .deb files.  I found out I can not have a real-time kernel due to having an Nvidia gpu, so now I am trying to undone what I have done today :(. I do not have a back-up of my ubuntu, I do have one from my ROS workspace, which is the only important thing I have in Ubuntu. But I have installed quite a few things, updates, software to get my ROS project working. 
In kernel 4.16, my second monitor is not working anymore, and some things changed (because of my attempt to upgrade my kernel, I don't know what I changed exactly), which caused some ROS parts to not work anymore. In kernel 4.15 my wifi is broken, I can not connect to a network, and my sound is broken as well. 

Could someone guide me in a direction so I can restore what I have done? What would be the proper way to restore it? 
If I forgot to provide relevant information I can post that. 

Thank you very much in advance. 

Kind regards, 
Not Katy Perry

---

### Post by TheFu on 2021-01-20
linux-headers-**4.14.12-rt10**_*.deb and linux-image-**4.14.12-rt10**_*.deb
seem like the wrong names to be seeking.  Maybe something with the kernel version you just built would make more sense?  Wasn't that **4.16**, not 4.14?

Support for 16.04 ends in a few months. We've had a good run.  I started migrating my last 16.04 systems to 18.04 + HWE kernels last week.  None went smoothly, but the things I was most worried about DID get handled correctly.  The problems were a little nasty - first do-release-upgrade refused to work, so I had to drop back to the debian release upgrade method.  One system refused to boot after about 90 minutes of package upgrades. Seems one of the file systems got corrupted.  A quick fsck and that was better ... but it has run out of space in /boot (a separate partition on that machine), so I had to boot from an old kernel and fix that.

Of course, if it had been really bad, I'd just restore from backups.  I have automatic, daily, versioned, backups for all but toy systems here.  But I don't actually backup the core OS or kernels.  Those are easily re-installed from the 50-quazillion ISO files on the internet. I always have a few flash drives that can boot a few different Linuxen.  Used one last July when a boot disk on my DLNA server died for the few days when as a replacement HDD was shipped. Booted a Live Ubuntu-Mate desktop, installed about 10 programs into the "live environment" and we got back to enjoying our evenings again.

**Backups - there aren't any substitutes.**

In general, a fresh Ubuntu install is 10-15 minutes.  Patching that is 1-5 minutes more.  Restoring /home/, /usr/local/ and selected parts of /etc/ is about 15 minutes more.  The last thing is to take a list of manually installed APT packages from the prior system (yes, plan ahead for this), then feed that list into APT to reinstall those manually installed packages on the new system.  That takes about 15 minutes.  So ... in 45 minutes total, you have a system that for all practical purposes **is** the same as the one that failed.

There are plenty of advanced ways to make system upgrades less risky, but these require using snapshots with advanced volume management tools like ZFS or LVM ---- and have the ability to plan ahead and make a snapshot prior to performing any upgrades, do the upgrades, leaving the snapshot around for a few days until you are certain the upgrade went well.  None of this is hard, but if you don't know about it, you'll never use it.  Snapshots are very handy for ensuring non-corrupted  backups too.
aljames2 script w/ LVM snapshots:
[https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)
Script:
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) has more discussion.

Restoring backups:
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

Or if you want to keep it bonehead simple, but accept different risks, 
rsnapshot: rsync + hardlinks for versioned backups (requires Linux file system like ext4)
[https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)

Regardless - everything begins with having a flash USB drive with whatever Ubuntu-desktop you prefer to go into the non-working system and make fixes.  Start there.  Basically, create an Ubuntu Installer flash drive ... but choose "Try Ubuntu" at the prompt, not "install".

---

### Post by grahammechanical on 2021-01-20
Do you get a Grub boot menu? Can you select Advanced Options for Ubuntu? Under Advanced Options you will see some earlier Linux kernels that you can still boot into. May be one of them will get you to a working desktop. From there you need to remove the broken kernel that you tried to install.

Regards

---

### Post by katyperry78 on 2021-01-21
Thank you for the suggestions. 

@TheFu 
I did change the version in the .deb files, so I tried: sudo dpkg -i ../linux-headers-4.16.18-rt12_*.deb ../linux-image-4.16.18-rt12_*.deb, which did not work. No .deb found was the error. I don't know if this kernel is possible with an Nvidia gpu. I will look into Ubuntu 20.04 and see if ROS Noetic has the things I need. 
And I am certainly going to back things up haha. 

@grahammechanical
Yes I can get into the Grub menu. I can boot windows fine. I can go to advanced options for ubuntu and boot kernel 4.04, 4.14, 4.15 and 4.16. I had 4.15 before all this trouble, but in that kernel, my wifi and sound is now broken (worked before all this). In 4.16 my dual monitor does not work (yet?), which might be the easiest to resolve.

Thanks

---

### Post by TheFu on 2021-01-21
> **katyperry78 said:**
>   No .deb found was the error. 

Did the compile, link, and creation of the .deb files actually work?  Any previous errors?
Or could they have just been placed somewhere else?

---

### Post by katyperry78 on 2021-01-22
@TheFu In the guide I referred to, 
fakeroot make -j4 deb-pkgcommand still worked. The command after that for the .deb files did not. I don't know in which step of the guide the .deb files are created, I do not have enough linux experience for that.

---

### Post by TheFu on 2021-01-22
> **katyperry78 said:**
> @TheFu In the guide I referred to, 
fakeroot make -j4 deb-pkgcommand still worked. The command after that for the .deb files did not. I don't know in which step of the guide the .deb files are created, I do not have enough linux experience for that.

Use the 'ls' command to see if the .deb files exist.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good beginner book.

---

### Post by katyperry78 on 2021-01-28
Sorry for the long wait. 
in my home folder, ls gives:
backup_workspace.zip
catkin_ws
Desktop
Documents
Downloads
examples.desktop
frames.gv
frames.pdf
freenect2
Kinect_dingetjes
libfranka
libfreenect2
linux-4.14.12.tar.xz
linux-4.16.0.tar.sign
linux-4.16.0.tar.xz
linux-4.16.18
linux-4.16.18-rt12_4.16.18-rt12-1_amd64.changes
linux-4.16.18-rt12_4.16.18-rt12-1.debian.tar.gz
linux-4.16.18-rt12_4.16.18-rt12-1.dsc
linux-4.16.18-rt12_4.16.18-rt12.orig.tar.gz
linux-4.16.18.tar
linux-4.16.18.tar.sign
linux-headers-4.14.0-041400_4.14.0-041400.201711122031_all.deb
linux-headers-4.14.0-041400_4.14.0-041400.201711122031_all.deb.1
linux-headers-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb
linux-headers-4.16.18-rt12_4.16.18-rt12-1_amd64.deb
linux-image-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb
linux-image-4.16.18-rt12_4.16.18-rt12-1_amd64.deb
linux-image-4.16.18-rt12-dbg_4.16.18-rt12-1_amd64.deb
linux-libc-dev_4.16.18-rt12-1_amd64.deb
Music
patch-4.16.0-rt10.patch.sign
patch-4.16.0-rt10.patch.xz
patch-4.16.0-rt12.patch.xz
patch-4.16.12-rt12.patch.xz
patch-4.16.18-rt12.patch
patch-4.16.18-rt12.patch.patch.xz
patch-4.16.18-rt12.patch.sign
patch-4.16.18-rt18.patch.sign
patch-4.16.18-rt18.patch.xz
patches-4.16.18-rt12.tar.sign
patches-4.16.18-rt12.tar.xz
pcl
Pictures
Public
ros tutorial trash
Templates
Videos
ws_bakcup_19_01_2021.zip
ws_moveit



So I think they are there. 

When I run uname -r, I get: 4.16.0-041600-generic
I don't need 4.16  specifically anymore. What would be the best way to restore this or an older kernel? 

Kind regards

---

### Post by TheFu on 2021-01-28
In the terminal, change directory into where the .deb files exist. Run:
```
sudo apt install ./linux-image-4.16.18-rt12_4.16.18-rt12-1_amd64.deb
```
Note the exact path to the deb filename. That is required.  You can use the full-path or another relative-path to the deb file if you don't want to change directories.

---

### Post by katyperry78 on 2021-01-31
I was able to install it, after reboot my kernel was 4.16.18 rt12.
My second screen still did not work. 
I tried reinstalling the NVidia driver, but some file was missing during the process, and now I am  not able to login any more. I think I will install ubuntu 18.04, it seems like the easiest option. Or do you have another suggestion?
Thank you for your help and I am going to take a look at the book you recommended.

Kind regards

---

### Post by TheFu on 2021-01-31
> but some file was missing during the process
You'll need to solve that. Those pesky error messages are full of useful information. READ THEM.

---


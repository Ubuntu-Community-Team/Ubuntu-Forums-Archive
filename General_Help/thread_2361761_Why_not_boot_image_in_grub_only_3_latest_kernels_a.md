---
title: "Why not boot image in grub only 3 latest kernels as default ??"
date: 2017-05-20
forum: General Help
---

### Post by henke54 on 2017-05-20
"Common" users (not tech-savy) ,like me, have sometimes an "error" by booting, that says ; "The volume "boot" has only 0 bytes disk space remaining".
That is because all the kernel-updates are kept in grub.
I do not see any reason why ALL the kernel updates are kept, [COLOR="#FF0000"][SIZE=3]INSTEAD OF ONLY THE LAST 3 BY DEFAULT[/SIZE][/COLOR] ?????
And i am not alone it seems ->[https://ubuntuforums.org/search.php?searchid=15079439](https://ubuntuforums.org/search.php?searchid=15079439)
:confused:

---

### Post by oldfred on 2017-05-20
House keeping was always considered something the user should do.
And most do not have a separate /boot, but if you have LVM which is more advanced then you have the separate /boot. Since more advanced they assume you know to houseclean.

But there must be a million threads on this issue. And issue became worse as they started to auto download both standard and signed versions of kernels.
This has been fixed in 16.04. I only have two kernels after an new one is downloaded.

What version of Ubuntu?

       /boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
Check current kernel I also keep one older just in case & I typically preferred synaptic when I had to manually do it:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do
sudo apt-get -s autoremove 


 kernel files by version  - initrd, vmlinuz, abi, system.map
With 14.04 this should keep two kernels on new kernel installs:
/etc/kernel/postinst.d/apt-auto-removal

---

### Post by henke54 on 2017-05-21
> **oldfred said:**
> What version of Ubuntu?

I have version 16.04, which was upgraded from 14.04.

The problem I had was exactly the same as following ; [Kernels not autoremoving, causing out of space error on LVM or Encrypted installation or on any installation, when /boot partition gets full ](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093)
It seems that this "bug" is "persistent", because that bug is reported by Elfy on 2014-08-14 and the last post on that thread is from 2017-04-27.

I see on that thread , that this bug is fixed, and still , i got it . ..... :confused::confused:

---

### Post by oldfred on 2017-05-21
I do not know but think those that upgraded from 14.04 to 16.04 seem to have issue. I did a new clean install and do not have the issue.

Did you houseclean all the old kernels from 14.04 before upgrade? The newer dpkg with 16.04 will not know about those old kernels since it did not install them. So those may still be in /Boot and grub menu? But really are just for 14.04. 
And even if housecleaned you probably have at least 2 old kernels.

Did you look at this:
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
> In Ubuntu 14.04 only kernels installed by Unattended Upgrades are marked as being automatically installed. 

---

### Post by henke54 on 2017-05-21
Thank you oldfred for answering ;) .
My problem is solved by someone who is really tech-savy in linux(=my son  :p ) , but, my question is now ; is it now "in future" so, that by DEFAULT, the old kernels(but 3 ... or so), are removed "automatically" ??

---

### Post by Dennis N on 2017-05-21
I think to get automatic autoremoval, you need unattended upgrades working. I don't use unattended upgrades, so I make a point to remember to follow the "install one and remove one" philosophy. I leave 3.

Some distros like Fedora always keep three kernels no matter how you upgrade, automatically erasing the oldest. There are no "unattended upgrades" options there. Manjaro keeps only one in each series, plus a "fallback" (which possibly is the previous one - not sure about that). But you can also have several series installed together eg: 3.16, 4.4, 4.10.

---

### Post by oldfred on 2017-05-21
With clean install of 16.04 I have check for updates daily, but do not have auto install on.
System settings, Software & updates, updates tab.

And it only keeps 2 kernels when I do run the updates.

---

### Post by Keith_Helms on 2017-05-21
I just checked and my Xubuntu 16.04 system has 7 kernels installed.   This was a fresh 16.04 install, not an upgrade from 14.04.

NOTE:  I just ran apt-get autoremove and that deleted the 5 oldest of the 7 kernels and got me down to 2.  It appears that command does not run as part of software updates.  I have my updates set to display immediately for security updates and display weekly for other updates.   I generally just let it run when the software updater window pops up, unless I'm on a slow connection somewhere away from home.

---

### Post by Dennis N on 2017-05-21
> I just checked and my Xubuntu 16.04 system has 7 kernels installed.   This was a fresh 16.04 install, not an upgrade from 14.04.
The new kernel needs to be installed with unattended upgrades*, otherwise, automatic removal of oldest kernel isn't done.

*to use this feature, set security updates to be downloaded and installed automatically.

---


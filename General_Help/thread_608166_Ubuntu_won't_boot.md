---
title: "Ubuntu won't boot"
date: 2007-11-09
forum: General Help
---

### Post by dpholmes on 2007-11-09
So, I had been running Gutsy for about 2 weeks now without any problems.  Yesterday I tried to shut the computer down and going to "shut down" just brought me to the log-in screen.  This happened a few times in a row, and from the log-in screen my only option was to "suspend" which didn't work either.  So i turned it off cold, I know that's not good, but I had to get my computer off right then.

Today, when trying to boot, it hung and upon further review it hung with the error message:
Target filesystem doesn't have /sbin/init

So, I found on a few message boards that i needed to reinstall udev, which i tried via the liveCD:
sudo mount -t ext3 -o rw /dev/sda3 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev
(i also tried apt-get --reinstall install udev, same error)

Each time I get this error:
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.2-1ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I found a couple forums that said i should check to make sure /boot/grub/menu.lst pointed the boot list to the proper device, but I can't find that file on my filesystem. 

Thanks for your help in advance,
-Doug

---

### Post by por100pre1 on 2007-11-09
Try this:

```
sudo apt-get install -f
```

---

### Post by dpholmes on 2007-11-09
Thanks, same error though.  Here's a more detailed error message:
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.2-1ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Maestro23 on 2007-11-09
> **dpholmes said:**
> Thanks, same error though.  Here's a more detailed error message:
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.2-1ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Goto /var/cache/apt/archives and delete the cupsys package

> cd /var/cache/apt/archives

ls (list contents of directory)

sudo apt-get --purge remove cupsys_1.3.2-1ubuntu7_i386

or 

sudo dpkg -P cupsys_1.3.2-1ubuntu7_i386

then

sudo apt-get update && sudo apt-get upgrade


---

### Post by dpholmes on 2007-11-09
So, I get an interesting error here, when i "ls" these are packages listed that involve cupsys:
cupsys_1.3.2-1ubuntu7.1_i386.deb
cupsys_1.3.2-1ubuntu7_i386.deb
cupsys-bsd_1.3.2-1ubuntu7.1_i386.deb
cupsys-client_1.3.2-1ubuntu7.1_i386.deb
cupsys-common_1.3.2-1ubuntu7.1_all.deb

looks good right? well when i try:
 sudo apt-get --purge remove cupsys_1.3.2-1ubuntu7_i386.deb 
i get this error:
 E: Couldn't find package cupsys_1.3.2-1ubuntu7_i386.deb

and when i try:
 sudo dpkg -P cupsys_1.3.2-1ubuntu7_i386
i get this error:
 dpkg - warning: ignoring request to remove cupsys_1.3.2-1ubuntu7_i386 which isn't installed.

does this mean i should be trying to remove cupsys_1.3.2-1ubuntu7.1_i386 ?
i'd rather not do this w/o someone confirming it, as i have no idea what it'd do.

---

### Post by dpholmes on 2007-11-10
So, I noticed something else while running sudo apt-get update; apt-get upgrade; apt-get install udev .  Here is a more detailed error report:

The following packages will be upgraded:
  cupsys
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
30 not fully installed or removed.
Need to get 0B/2017kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 121202 files and directories currently installed.)
Preparing to replace cupsys 1.3.2-1ubuntu7 (using .../cupsys_1.3.2-1ubuntu7.1_i386.deb) ...
Ignoring nonregistered document cupsys
/usr/sbin/invoke-rc.d: 274: /sbin/runlevel: not found
invoke-rc.d: initscript cupsys, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/usr/sbin/invoke-rc.d: 274: /sbin/runlevel: not found
invoke-rc.d: initscript cupsys, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/cupsys_1.3.2-1ubuntu7.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1

---

### Post by dpholmes on 2007-11-10
should i just reinstall ubuntu? this seems like an impractical solution.

---

### Post by Maestro23 on 2007-11-10
> **dpholmes said:**
> should i just reinstall ubuntu? this seems like an impractical solution.

Try to delete all the .deb in the archive.

> sudo dpkg -P *.deb

---

### Post by dpholmes on 2007-11-10
> root@ubuntu:/var/cache/apt/archives# sudo dpkg -P *.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in


any thoughts?

---

### Post by dpholmes on 2007-11-11
since the package is uninstalled, is there any other way to remove it, besides apt-get & dpkg?

---


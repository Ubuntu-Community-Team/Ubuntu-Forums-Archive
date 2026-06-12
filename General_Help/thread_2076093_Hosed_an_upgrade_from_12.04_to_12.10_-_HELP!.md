---
title: "Hosed an upgrade from 12.04 to 12.10 - HELP!"
date: 2012-10-25
forum: General Help
---

### Post by renegadeandy on 2012-10-25
Hi.

An upgrade was running between 12.04 and 12.10 when something went wrong and the PC crashed.  When attempting to boot normally it would then just hang after starting rtvscand.

I therefore used grub to enter the recovery mode, dropped to a root prompt, remounted with read write, and ran sudo dpkg --configure -a. This ran for a long time, and then failed with the following an error which listed which packages it couldnt configure , stuff like :

update-manager-core, update manager etc, all update manager stuff.

So i restart, and my grub menu has changed,now i only see Ubuntu, 2 x memtests and my windows 7. SO I select Ubuntu and when booting it gets to :

> Starting x display manager
./build.sh --kernel-dir //lib/modules/3.5.0-17-generic/build --kernel-rel 3.5.0-17 generic bad exit status 1
Error (dkms apport) 
Error! bad return status for module build on kernel 3.5.0-17-generic(i686)
**starts lots of stuff
Starting rtvscand [done]
*Checking battery state - 


And then it hangs, I cannot get to another terminal, I cannot type, the whole thing is locked up. Now i dont know what to do, as I cannot get to recovery mode, I cannot boot normally!

Somebody help!

---

### Post by jerrrys on 2012-10-25
Could you use the live cd and remove 3.5.0-17 and let it fall back to the previous kernel.

---

### Post by renegadeandy on 2012-10-25
Yes I could, downloading one now.

Not sure if i should though, doing an ls of /boot and all i see is grub folder, and one init.rd img.

What command do I use to remove the kernel?

---

### Post by oldfred on 2012-10-25
Do you have proprietary video drivers? nVidia or fglrx? 

12.10 does not download headers and then video does not install correctly. That almost looks like what your failure was. 

I might try chrooting into your install, do updates and install headers.

Some ways to chroot if not familar:
[Boot-Repair] Graphical tool to repair the PC boot in 1 clic !
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Then in chroot:
#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

#  if nvidia this works, but you need different commands for other video.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that: 
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current

apt-get -f install
dpkg --configure -a

---

### Post by YannBuntu on 2012-10-25
> **oldfred said:**
> Some ways to chroot if not familar:
[Boot-Repair] Graphical tool to repair the PC boot in 1 clic !
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

B-R helps doing chroot only when using the "Purge GRUB" option. (But that's not really what this option was designed for ;) )

---


---
title: "Can't find files filling disk"
date: 2019-08-13
forum: General Help
---

### Post by bruce-hyatt on 2019-08-13
I have Ubuntu Server 14.04 on an old HP Compaq 5750 SFF with 1 GB of memory. I use it as a Samba server. It has an 80GB HD and the files are stored on a 1TB external drive. That drive was corrupted and when trying to recover files from it using testdisk I accidentally ran the program from the 80 GB HD. As a result, my HD appears to be full of recovery files created by testdisk. But I cannot find the files to delete them. I used du in a number of ways but couldn't find them. Some of the more-powerful searches failed because of the lack of disk space.

It also appears to be preventing me from repairing or reinstalling Ubuntu. I can't boot the installation image from the CDROM nor from a USB stick. When I tried to make a new mount point for the CDROM to determine if it's working, it failed returning "cannot create directory. No space left on disk." And that got me to thinking; the installation probably needs disk space, though I would think I would have gotten an error message if that was the problem. Instead it always boots the existing kernel.

Actually,I 'm not 100% certain that it was running test disk that caused the problem but I can't think what else could have filled the disk to 100%.

How can I free up some space to try to repair/reinstall Ubuntu?

Thanks in advance,
Bruce

---

### Post by Impavidus on 2019-08-14
The computer should let you boot a live disk (dvd or usb) no matter whether the hard drive is fine, full, empty, broken or absent. A full hard drive won't block a fresh install. So something else must be going on. Anyway, 14.04 is no longer supported, so you need that fresh install.

But first rescue your files. Use a live disk or plug your external drive into a different computer.

---

### Post by guiverc on 2019-08-14
I agree with @Impavidus, ie. you should move to a supported release of Ubuntu, or if you should be using Ubuntu 14.04 ESM - use your Ubuntu Advantage support as you're paying for it, and I cannot see how a full disk would prevent re-install.

When trying to find where your space was used (eg. `du`, `df` etc) did you remember to check for inodes (--inodes), though from your description I'd bet you have more problems than just space.

---

### Post by dragonfly41 on 2019-08-14
> [COLOR=#000000]Actually,I 'm not 100% certain that it was running test disk that caused the problem but I can't think what else could have filled the disk to 100%.[/COLOR]
One possibility is that you setup testdisk to save testdisk recovered files in the now full disk you have. When using testdisk you should target another disk such as external preformatted (ext4 partition)  USB drive to receive/store any recovered files.  Apart from space considerations you do not want to overwrite the files you are trying to recover.  In fact it is better to run testdisk installed in a *persistent* LiveUSB. to receive recovered files

---

### Post by TheFu on 2019-08-14
More self-inflicted problems that having backups would have completely avoided. testdisk and/or photorec are problems best avoided.  Learn from this.

14.04 standard, free, supported ended earlier this year.  Upgrading to a new release would have been easier if done BEFORE support ended.  Lots of people trying after support ended are having issues.  Moving to 18.04 is the best choice at this point.  Servers should only run LTS releases, except under extraordinary reasons.

Boot from a USB live-boot install,  use a desktop version of Ubuntu (the DE doesn't matter, whatever you like).  
Mount all the partitions on the directly connected disks.  I'd mount them under /mnt/ for this temporary purpose.
Run **df -h** and **df -i** to see which partitions are 100% used.
To find big files, use **find**.
```
sudo find /path/to/each/mount -type f -size +1G -print
```
If that doesn't find any large files, change the size to *+500M*, then *+250M* .... 
You can also search by file name ... *-iname \*mov* or create date *-ctime* and you can use AND and/or OR connectors for some binary logic in how **find** works.
Copy off the files you want to keep.  Don't forget to get everything in /etc/ and /usr/local/.  There could be files under /var/lib/ that you need too.  The server admin should know where these files are located.
After you get /var and / to have a little free space, 1-2G should be enough, boot back into the normal OS and make a list of installed packages using apt-mark.
```
apt-mark showauto | tee $local_backup/apt-mark.auto
apt-mark showmanual | tee $local_backup/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark auto $(cat apt-mark.auto )
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

```
Copy those files with the list of packages off.  The plan is to do a fresh 18.04 install, then use the "manually" installed list to have the fresh install load those into the new OS install.  Some won't exist in 18.04, but most will.  The automatic list shouldn't be needed, since dependencies will be a little different for the different packages.

When you copy off the files, be certain that the permissions are retained - owner, group, and all the rwx stuff plus any ACLs.  None Linux file systems will drop that information.  Probably cannot copy/back up the files without using sudo, or the ownership+group will be lost.

---


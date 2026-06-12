---
title: "Can't boot into Ubuntu 14.10"
date: 2015-02-07
forum: General Help
---

### Post by rugile on 2015-02-07
Hey guys, so I've been unable to boot into Ubuntu 14.10 lately - when I try to boot, it gives me the following error message: 
> Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

So I boot into bootable USB with Ubuntu and perform fdisk -l, and this is the output:

>    
Device    Boot      Start                  End                 Blocks       Id     System
/dev/sda1   *            2048           206847            102400         7     HPFS/NTFS/exFAT
/dev/sda2             116576254     362338303   122881025    5     Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3              20998144     116574207     47788032  7     HPFS/NTFS/exFAT
/dev/sda4             362338304    976773167    307217432    7      HPFS/NTFS/exFAT
/dev/sda5             116576256    120479743     1951744      82    Linux swap / Solaris
/dev/sda6             120481792    362338303    120928256   83    Linux


I then tried the following command:

sudo e2fsck -f -y -v /dev/sda6

which performed and fixed many errors (after pressing 'y' many times), though didn't really make Ubuntu boot. I realize that maybe I have to fix the /dev/sda1 partition somehow (since it is the boot partition), but I am unable to do it under bootable usb (because it is NTFS, and fsck won't work), and I don't know the workaround for this.

I am using dual boot with Windows 7 and Ubuntu 14.10.

Any help appreciated! This problem is really frustrating.

---

### Post by ajgreeny on 2015-02-07
Have a look at Boot-Repair in my signature and run that in a live Ubuntu system (the one you used to install it) but do not run the default repair that may be offered; just copy the pastebin link it gives you for  the boot-info results, and paste that link back here.

---

### Post by rugile on 2015-02-07
Thank you for your answer! 

It did not generate a pastebin link (due to the absence of gawk and patebinit packages), but it generated a results text file, so I put that into pastebin. Here's the link:

[http://pastebin.com/7DzKiJ1A](http://pastebin.com/7DzKiJ1A)

---

### Post by oldfred on 2015-02-07
Your sda6 is 99% full with only 1.3GB available.

The init file is the last thing created on a new kernel download as it is the boot image initially loaded.
So It seems an update must not have completed? But the issue may be that you do not have enough room to update?

I would houseclean some file in sda6, and/or chroot into it to clear out some old logs or do other housekeeping.
Boot-Repair does a basic chroot when you have it do the full uninstall/reinstall of grub.

 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

      
 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by rugile on 2015-02-07
Thank your for the answer!

Just to clarify - basically cleaning up the filesystem a bit and purging & reinstalling grub could be enough? Will do that as the first thing in the morning!

---

### Post by oldfred on 2015-02-07
I think when Boot-Repair does the full uninstall/reinstall of grub it also installs the latest kernel & then should fully update.

---

### Post by rugile on 2015-02-08
I tried what you recommended, but I cannot make the boot-repair do full GRUB reinstall - I cannot access any settings related to GRUB in its advanced settings (GRUB tabs are grey and do not contain anything). I tried following this tutorial: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) , but I did not go far, since after chrooting it says "I have no name!@ubuntu" instead of "root@ubuntu" as well as "bash: groups: command not found". I'll try downloading boot-repair-disk now, and see if it will help, but I really have some doubts about that

---

### Post by rugile on 2015-02-08
Okay well, the boot-repair-disk gave the same result as using it under Ubuntu LiveCD. I did the recommended repair by boot-repair, so now when I'm booting instead of grub I get Windows bootloader with the choice of NeoGrub bootloader (which doesn't work). I suppose now I should reinstall grub, but how do I fix the "I have no name!@ubuntu" problem?

---

### Post by oldfred on 2015-02-08
If Boot-Repair did not reinstall grub, then it could not see your Linux partition or install. Post link from Summary report.

Boot-Repair installs SysLinux as the Windows boot loader, so I do not know where you are getting NeoGrub from, did you install EasyBCD?

---

### Post by rugile on 2015-02-09
Here's the summary link:
[http://paste.ubuntu.com/10129602/](http://paste.ubuntu.com/10129602/)

Yes indeed, I have installed easyBCD previously (while repairing some booting problem that has occured some years ago).

---

### Post by oldfred on 2015-02-09
If you move boot flag back to sda1 with gparted or Windows repair disk (set active on), then Windows should boot or be repairable.
Boot-Repair did this which was wrong. Command line version of moving boot flag to sda6 which never would be correct (unless using Lilo).
parted /dev/sda set 6 boot on

Grub does not use boot flag. And Windows has to have boot flag on partition with its bootable files to boot or be repaired.

---

### Post by rugile on 2015-02-09
Windows does boot. I'm really confused about what should I do now...

---

### Post by oldfred on 2015-02-09
Then are you only booting Windows thru grub menu? Or was boot flag already moved.

My previous suggestion was a full uninstall/reinstall of grub not the auto fix option.

---

### Post by rugile on 2015-02-09
I am booting through Windows bootloader right now (no grub). I am not sure about the boot flag - how could I check it? 
I did try to completely reinstall grub, but I faced a problem I described before - after Chrooting into the original OS, it does not recognize itself as "root", and says " I don't have a name" instead, also, bash cant find any commands. So I bumped into a wall right here, and couldn't google myself out of it as eell

---

### Post by oldfred on 2015-02-09
Boot flag is the little * that you see if you list partitions with fdisk or parted.

If your original fsck had lots of errors perhaps you need to rerun it? Or is hard drive dying?

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your Linux ext type partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

---

### Post by rugile on 2015-02-09
Thank you for all the help once again.

Currently the boot flag is moved to the Windows partition then. Will see into the possibility that hard drive is dying, which might actually be true..

I reran the e2fsck - still get the same Chroot error. Guess maybe I should be heading for a clean reinstall of Ubuntu..?

---

### Post by oldfred on 2015-02-09
Could you copy & paste (in code tags or # in Advanced Editor) the entire chroot that you do?

You can check hard drive in Disks or Disk Utility of older version of Ubuntu. With Disks you have to use the icon in upper right corner to find Smart Data. While it can run many tests, all I really know is passed is good and anything else is almost always a new drive.

---

### Post by Gvarelov on 2015-02-10
Reinstallation of GRUB, but this time onto the MBR might solve your problem. No need on reinstallation of Ubuntu, the problem will come back. I assume you already had Windows on your hard disk when you installed Ubuntu. You may want to check out the wiki guide on troubleshooting GRUB2:
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
Basically, it's :
```
sudo grub-install /dev/sda
```
with possibly some packages required before you go on installing GRUB to the MBR, to which installer would I assume point out. Pay attention to the syntax, notice the "/dev/sda" and not "/dev/sda*n*" where* n* is partition number. The reason this might help is that when GRUB is installed on a partition, it becomes subject to filesystem manipulations of the OS, like moving blocks around, defragmentation etc. By moving it to the MBR, GRUB isn't OS's subject anymore and all the addresses in its core image are retained correct. Windows will still boot and will show up at the boot menu, as GRUB 2 has OS prober scripts that search the system for installed OSes...

---

### Post by rugile on 2015-02-10
I'm not sure whether I should mount a seperate boot partition now (since the boot flag has moved), so I tried both ways. Here's the entire chroot without mounting seperate boot partition:

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf 
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
bash: groups: command not found
I have no name!@ubuntu:/# 

```

And this one's with seperate boot paritition:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp/boot
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf 
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
sudo: unable to execute /usr/sbin/chroot: Input/output error

```

I did unmount after the first time. Input/output error is a new thing also, didn't appear before..
And I checked the hard drive, it seems to be okay. That's a relief

---

### Post by rugile on 2015-02-10
> **Gvarelov said:**
> Reinstallation of GRUB, but this time onto the MBR might solve your problem. No need on reinstallation of Ubuntu, the problem will come back. I assume you already had Windows on your hard disk when you installed Ubuntu. You may want to check out the wiki guide on troubleshooting GRUB2:
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
Basically, it's :
```
sudo grub-install /dev/sda
```
with possibly some packages required before you go on installing GRUB to the MBR, to which installer would I assume point out. Pay attention to the syntax, notice the "/dev/sda" and not "/dev/sda*n*" where* n* is partition number. The reason this might help is that when GRUB is installed on a partition, it becomes subject to filesystem manipulations of the OS, like moving blocks around, defragmentation etc. By moving it to the MBR, GRUB isn't OS's subject anymore and all the addresses in its core image are retained correct. Windows will still boot and will show up at the boot menu, as GRUB 2 has OS prober scripts that search the system for installed OSes...

I tried this, but it just said

```

/usr/sbin/grub-probe: error: failed to get canonical path of /cow.
```
Shouldn't I mount /dev/sda6 (and possibly the /dev/sda1 as a seperate boot partition?? I don't know about that, since the boot flag is now moved..) first, and then run the command as 
```
sudo grub-install --root-directory=/mnt/temp /dev/sda
```?
I'm just not sure what to do with the boot partition. Because the /dev/sda6/boot looks like a boot folder (with kernel images and stuff), while /dev/sda1/boot doesn't..

---

### Post by oldfred on 2015-02-10
Do not confuse a boot flag or a Windows boot partition which is NTFS formatted, with a Linux formatted /boot partition. Most desktops do not have nor need a separate /boot partition. Servers or some with server type configurations may need a /boot as a separate partition. Also some very old BIOS need a /boot partition or all of / (root) fully inside the first 137GB of a drive.

The install directions above assume you have already booted into your system, either manually or perhaps with Super Grub or other tools.
Boot-Repair will reinstall grub, but partition has to be working, so it can mount it. If you can now see your files then I would expect Boot-Repair to work

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by rugile on 2015-02-10
I do see my files, but Boot-Repair seems not to be working.

So I booted into liveCD and performed the commands you specified. GRUB is back, but we're still on square 1, with the initial error:

```

Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

```

---

### Post by oldfred on 2015-02-10
Did you do the full purge & reinstall of grub from Boot-Repair. I thought that would add the newest kernel and rebuild initrd boot file. 

If not then I am not sure what issue is. But I assume it was from your sda6 partition being too full to fully install the first time.

---

### Post by rugile on 2015-02-10
I couldn't do it, because it wouldn't give me the choice of that (as before, the GRUB tabs in Boot-Repair menu were grey and empty).

Would you think that reinstalling Ubuntu could fix the problem?

Thanks for all the help!

---

### Post by oldfred on 2015-02-10
You can do a full re-install relatively easily as long as you now have room. But you must use Something Else and choose same / (root) partition. It will overwrite all your current data so be sure to have good backups. There is a "dirty" install that only overwrites the install files but that will also overwrite system settings & user settings with the defaults. But your files should remain. Still best to have full backup.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

    
 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by rugile on 2015-02-12
So I reinstalled Ubuntu today, and it works well now! It feels nice to have Ubuntu back!
Thank you for the great help once again!!

---

### Post by oldfred on 2015-02-12
Glad you got it working. :)

You can also change to Solved.

---


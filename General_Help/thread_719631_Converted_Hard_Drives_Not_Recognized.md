---
title: "Converted Hard Drives Not Recognized"
date: 2008-03-09
forum: General Help
---

### Post by oldefoxx on 2008-03-09
Using Ubuntu 7.10, and everything fine until I decided to convert some FAT32 partitions to NTFS.  Now Ubuntu is unable to recognize those drives.  It there a way I can get Ubuntu to recognize those drives on its own, manual changes I can make to help it, or do I have to reinstall Ubuntu to make this happen?

---

### Post by taurus on 2008-03-09
Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
cat /etc/fstab
df -h
```

That is a lower case letter L, not number 1.

---

### Post by oldefoxx on 2008-03-09
oldefoxx@oldefoxx-desktop:~$ sudo -s
[sudo] password for oldefoxx:
root@oldefoxx-desktop:~# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x3b3d3b3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5096    38525728+   7  HPFS/NTFS
/dev/sda2            5097       20673   117762120    f  W95 Ext'd (LBA)
/dev/sda5            5097       10243    38911288+   7  HPFS/NTFS
/dev/sda6           10244       15390    38911288+   7  HPFS/NTFS
/dev/sda7           15391       20673    39939448+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x84fe419e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6096    46085728+  83  Linux
/dev/sdb2            6097       12191    46078200   83  Linux
/dev/sdb3           12192       18286    46078200   83  Linux
/dev/sdb4           18287       41345   174326009    f  W95 Ext'd (LBA)
/dev/sdb5           18287       40638   168981088+   7  HPFS/NTFS
/dev/sdb6           40639       40868     1738768+  82  Linux swap / Solaris
/dev/sdb7           40869       41098     1738768+  82  Linux swap / Solaris
/dev/sdb8           41099       41345     1867288+  82  Linux swap / Solaris
root@oldefoxx-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=979a2071-d3a8-4ad1-bcab-aaa3b06b5921 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=82049D00049CF7FD /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=3E4C-36C5  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=3E63-3A43  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=7C99-ECBA  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=a896bafe-097c-400c-9cb1-24a56d1c0aa9 /media/sdb2     ext3    defaults        0       2
# /dev/sdb3
UUID=d9fad3fb-a74c-4e7e-be6f-b45bdbff0ae0 /media/sdb3     ext3    defaults        0       2
# /dev/sdb5
UUID=C8065F6B065F5A10 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=42ca1a2e-9382-448a-93de-a92bee99128e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec  0       0
none            /proc/bus/usb   usbfs devgid=46,devmode=664  0       0
root@oldefoxx-desktop:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              44G  8.7G   33G  22% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  148K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              37G   28G  9.4G  75% /media/sda1
/dev/sdb2              44G  2.9G   39G   8% /media/sdb2
/dev/sdb3              44G  3.0G   39G   8% /media/sdb3
/dev/sdb5             162G   68G   95G  42% /media/sdb5
root@oldefoxx-desktop:~#

---

### Post by taurus on 2008-03-09
Are you talking about the /dev/sda5, /dev/sda6, & /dev/sda7?

First, make a backup copy of your /etc/fstab.

```
cp /etc/fstab /etc/fstab.bak
```
Then, edit /etc/fstab

```
nano /etc/fstab
```
and replace these lines

```

# /dev/sda5
UUID=3E4C-36C5 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda6
UUID=3E63-3A43 /media/sda6 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda7
UUID=7C99-ECBA /media/sda7 vfat defaults,utf8,umask=007,gid=46 0 1

```
with these.

```

# /dev/sda5
UUID=3E4C-36C5 /media/sda5 ntfs-3g defaults 0 0
# /dev/sda6
UUID=3E63-3A43 /media/sda6 ntfs-3g defaults 0 0
# /dev/sda7
UUID=7C99-ECBA /media/sda7 ntfs-3g defaults 0 0

```
Save the changes with <Ctrl>o and exit with <Ctrl>x.

Now, install ntfs-3g driver.

```
apt-get update
apt-get install ntfs-3g
```
You can either reboot your machine or remount those three partitions with

```
mount -a
df -h
```

p.s.  Since you log in as root, I assume you know what you are doing.  That's why I didn't include any sudo in front of those commands.

---

### Post by oldefoxx on 2008-03-09
Hmmm.  Afraid that does not work.  I made the changes, but when it tried the mount -a, I get these errors:

root@oldefoxx-desktop:~# mount -a
Failed to access '/dev/disk/by-uuid/3E4C-36C5': No such file or directory
Failed to access '/dev/disk/by-uuid/3E63-3A43': No such file or directory
Failed to access '/dev/disk/by-uuid/7C99-ECBA': No such file or directory
root@oldefoxx-desktop:~# 

I also tried the reboot, and the drives are not picked up then either. Perhaps the conversion changed the associated uuids for these drives, and I would have to know what they were changed to or replaced by.

---

### Post by mc4man on 2008-03-09
Your partitioning in sda looks odd. Did you delete and create a new  extended partition before setting up your new ntfs  ld's? I would probably use a gparted boot disk, delete the 3 ntfs partition (ld's) , delete the extended and then either create a new  extended with 3 ntfs ld's, or forget the extended and go with  3 new primaries. If you go with 3 primaries you could do it in windows disk man. instead 

edit:if now or in future you decide to use a gparted boot disk the force vesa option is the most likely to load
on second thought probably better to create your partitions or ld's in windows - that way you can easily name the volumes

---

### Post by oldefoxx on 2008-03-09
After some initial difficulties, I learned by trial and error that FAT32 or NTFS partitions are best set up using the Disk Manager in Windows.  In fact, if you want to have EXT2 or EXT3 partitions recognized later by Windows (with the EXT2 driver installed), or to include an NTSF partion amongst foreign partitions, is to prototype the foreign partitions as sell as the Windows-compatible partitions,  That is, set up the foreign partitons with the Disk Manager, but don;t bother formatting it.  Then when you install Ubuntu, you redesignate the foreign partition as EXT3 (unless you have a preference for another format).

So what you see in this "odd" configuration is something that Windows decided is appropriate.  It works very well, and both Windows and Ubuntu are able to access all partitions (although Windows does not see the swap partitions),  Some other more conventional efforts simply failed to work properly.

Note the inclusion of three swap partitions, an attempt to allocate a swap for each Ubuntu install,  I had hoped that doing this, and flagging nouse for two during each install, would avoid getting errors detected when booting to an alternate Ubuntu install.  I don't know if this really helped or not, of whether it is even doing what I intended.

When I installed Ubuntu, I set it up on sdb3, then seb2, then sdb1, as this caused the gurb menu.lst to be filled in in reverse order.  I could have edited menu.lst and changed the order manually, but I decided to just avoid that step.  the problem is, that later installs of Ubuntu seem to step on the previous ones, as when I boot to sdb2 or seb3 I get a disk error 8, and have to use Ctrl+D in order to continue the boot process.  I guess Ubuntu was never really meant to run in this fashion.  But that annoyance aside, it works pretty well.

However, I find it a bit disturbing that converting partitions from one form to another can throw Ubuntu (probably Linux in general) off in this fashion.  I tried the recovery mode when booting via grub, but that did not find and fix the problem.  Seems to me this would be where it could have been found and fixed automatically, and not deter the normal boot process.

---

### Post by taurus on 2008-03-09
Okay, let's get this clear up.  You can convert from whatever filesystem to whatever filesystem.  The only trouble is when you do that, the UUID for that partition would change so you need to use the new one to mount it if you decide to use UUID in /etc/fstab.  Therefore, you need to look up the new UUID for those three partitions in /dev/disk/by-uuid

```
ls -la /dev/diskby-uuid
```
and replace the old ones in /etc/fstab with the right ones from /dev/disk/by-uuid.

That's why you got an error about those three new ntfs partitions when you tried to mount them.

---

### Post by oldefoxx on 2008-03-09
The good news is that taking all the advice together, I now have the problem pretty well resolved.  I did depart from the recommendations to a certain degree, with the expectation that I might have to do it again exactly as suggested.  But this was unnecessary.

First, instead of installing ntfs-3g, I looked at the /etc/fstab information for /media/sdb5, which is also an NTFS partiton.  In fact I just cut and pasted the information after .media/sdb5 and used that for each of /media/seb5, /media/sdb6, and /media/sdb7.  Since I already knew that Ubuntu is working well with my NTFS volumes, I ignored the information about installing ntfs-3g as well.

Second, the information about listing /etc/dev/by-uuid gave me the other missing information.  I prefer using gedit over nano, as I am more comfortable with the way it works.  I used cut-and-paste again to copy the uuid from my terminal console window over to /etc/fstab, making not that the -> signified the volume in the terminal window.  Cut in the terminal window is done with Ctrl+Shift+C.  Paste in gedit can be donw with Ctrl+V, or Ctrl+Insert.  I usually use Ctrl+Insert, because only this works in the Terminal console, and I prefer standardizing where I can.  I saved the /etc/fstab file, and used mount -a, and df -h as suggested, and that showed the drives were accessable.  They also show up on my desktop.

I just wanted to detail a few things as a way to help others in case this problem comes up elsewhere.  Everything done in the terminal console was preceeded with a sudo -s to activate the superuser mode, giving me administrative rights.  I'm not the one that decided to use uuids in /etc/fstab, that is just the way Ubuntu configured itself when I Installed it.  But because you mentioned it, I decided to replace the whole UUID=[uuid] with the /dev/sd* associated with the particular drive,basing this on the way the cdrom drives are entered,  and that also worked.  I did this for all three Ubuntu installs, but ran into another odd problem with the install on /media/sdb3, which is that it keeps trying to access /media/sda7 as an EXT2 file system and getting an error, even though it is flagged as an ntsf file system in /etc/fstab (and properly accessed as such by Windows and by the Ubuntu installs on /media/sdb1 and /media/sdb2).  If nobody can tell my why this is happening, I may be forced to start over on /media/sdb3, because something is not right there.

---

### Post by oldefoxx on 2008-03-10
I had used True Image under Windows to create an archive of the /media/sdb3 partition earlier, so I used it again to restore the partition, then used gedit to go through and change the UUID= entires in the /etc/fstab file to the corresponding /dev/sd** designation instead (this was easy, since the commented line above give the device designation, and you can work from that).  This time when I attempted the mount -a, I got no errors from any of the partitions, so everything seems good to go.

Thanks for the great help, and the quick responses.

---


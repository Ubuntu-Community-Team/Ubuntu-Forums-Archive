---
title: "Hide second internal drive in file manager"
date: 2014-04-11
forum: General Help
---

### Post by samwillc on 2014-04-11
I have looked at a bunch of threads on how to do this but I'm still not 100% and would rather ask here than mess something up. I have win7 installed on a secondary internal HDD. I choose which drive to boot at startup using F8 and just boot into one or the other (linux as default), so no grub menu. Using elementary OS based on ubuntu 12.04 at the moment but will be trying out 14.04 shortly :))

In my file manager I have two more entries now since I installed the 2nd HDD:

DEVICES
File system (eOS)
System Reserved (win7 - 2nd HDD at '/media/80A02B83A02B7F32' << not sure if this is a temporary number or the actual UUID)
1.0 TB Filesystem (win7 - 2nd HDD at '/media/System Reserved')

I just want to hide the last two. I read about mounting at /mnt but not sure what do do exactly. Here is my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8cab14e5-d30e-4fbe-a5dd-0986c2138f9d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1da17164-7111-424b-8f3f-1ad425ef8edb none            swap    sw              0       0

```

Could somebody help me with achieving this. It's not a 'problem' per se that they're there, it's just that they don't need to be and I wouldn't want to accidentally mess up my win7 install on the other hard drive. I only use win7 for reaper and music stuff, nothing else, and I am the only user on this computer so no special permissions requirements. Thanks in advance.

Sam.

---

### Post by coldcritter64 on 2014-04-11
It **may** be possible to hide your partitions using gparted and setting a "hidden" or "diagnostics" flag for a Windows partition. 

I use this with other Linux install root partitions but use the "diagnostics" flag being a Linux formatted partition type to hide the filesystem completely from showing in Debian or Ubuntu working installs filebrowsers etc. 

It may work with either the hidden or diagnostic flag set on the partition if I recall correctly. I've only tested against ntfs and fat32 **storage **volumes, never against a working Windows partition. _*I have absolutely no idea how Windows will react to this idea, research it carefully before you try it*_. It worked for me to hide fat32 and ntfs formatted storage partitions of mine from different installations, may be of use to you. 

Cheers, coldcritter64

---

### Post by grumblebum2 on 2014-04-11
Don't know how this applies in your situation but in Ubuntu I can hide partitions with gnome-disks.
When applied it creates entries in fstab.
eg Using  gnome-disks I created these for my 2 windows partitions.One shows and one is hidden.
 ```
/dev/disk/by-uuid/F0D4A588D4A55220 /mnt/F0D4A588D4A55220 auto nosuid,nodev,nofail 0 0
/dev/disk/by-uuid/E0D8480AD847DE02 /mnt/E0D8480AD847DE02 auto nosuid,nodev,nofail,**x-gvfs-show** 0 0
```
Over my head but I suppose it depends if gvfs is used in elementary??

---

### Post by oldfred on 2014-04-11
If you want to remove boot entry in grub menu, you just need to turn off os-prober.

       sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

If you do not want to see partitions from Ubuntu, you have to mount them in fstab and make them not read/writeable. 

 Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

 [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

### Post by samwillc on 2014-04-12
Ok, this is what I did (using elementaryOS luna based on ubuntu 12.04).

Made a couple of directories under /mnt, one for win7 and one for system reserved:

```

sudo mkdir /mnt/win7
sudo mkdir /mnt/reserved

```

Found out the unique identifier for the second drive partitions (in my case /dev/sdb1 and /dev/sdb2):

```

sudo blkid
/dev/sda1: UUID="8cab14e5-d30e-4fbe-a5dd-0986c2138f9d" TYPE="ext4" 
/dev/sda5: UUID="1da17164-7111-424b-8f3f-1ad425ef8edb" TYPE="swap" 
/dev/sdb1: LABEL="System Reserved" UUID="8A4029F24029E5A3" TYPE="ntfs" 
/dev/sdb2: UUID="80A02B83A02B7F32" TYPE="ntfs"

```

Opened fstab for editing:

```

sudo nano /etc/fstab

```

Added these lines to the bottom using the directories that I created earlier (/mnt/reserved and /mnt/win7):

```

#hide windows 7 second hard drive
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

```

And now they are hidden. Hopefully this will help someone else with similar issue. I believe something different has to be done in 14.04 to achieve this but problem solved for now.

Thanks everyone :)

---


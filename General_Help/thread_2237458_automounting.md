---
title: "automounting"
date: 2014-08-01
forum: General Help
---

### Post by caligula2 on 2014-08-01
My HDD doesn't seem to want to automount. I go into the disks utility, go to the "Edit Mount Options," turn "Auto Mount Options" to off,  and then I am no longer able to mount it. I keep getting the error:

Error mounting system-managed device /dev/sda3: Command-line `mount "/mnt/Media"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 (udisks-error-quark, 0)

It works just fine if "Auto Mount Options" is on (except it doesn't automount). Does anyone have any ideas on how to fix this?

---

### Post by TheFu on 2014-08-02
Can you run fsck on the partition? Does that fix any errors?
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

### Post by caligula2 on 2014-08-04
fsck doesn;t seem to say anything is wron. Sorry about the slow respon. I wourk over 60 hr a week. I want my partition to automount so that xmbc will have access to my movies an files. like it did before I updated to the next ubuntu distro, and it ended up makeing a fresh install.

---

### Post by TheFu on 2014-08-04
> **caligula2 said:**
> fsck doesn;t seem to say anything is wron. Sorry about the slow respon. I wourk over 60 hr a week. I want my partition to automount so that xmbc will have access to my movies an files. like it did before I updated to the next ubuntu distro, and it ended up makeing a fresh install.

At least we know it isn't that.

I've never used the GUI to control mounting, so if you only want to work in that way, I cannot help.  
Are you interested in the CLI way?
Did you really mean to use the automounter (autofs) and understand how that works? It isn't the same as having the file system specified in the /etc/fstab.  If the disk is not always connected to this XBMC machine, then autofs makes sense, but if it is, I'd strongly recommend the /etc/fstab method instead.

I use autofs a bunch here, but only for sometimes connected storage or network storage. Hope that makes sense.

---

### Post by sp40140 on 2014-08-04
Could you confirm: Do you want to automount the drive?
Is it internal drive? If so, is it sata or ide? 
Also, when you say "it doesn't automount".. Do you see the icon for the drive in nautilus? if you do... what happens if you click on it?

---

### Post by caligula2 on 2014-08-04
The drive is always connected, so I would like to hear your /etc/fstab method.

I would like to automount the drive. It is internal sata. The icon does appear, but when I click on it I receive the error message:

Error mounting system-managed device /dev/sda3: Command-line `mount "/mnt/Media"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda3,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

(udisks-error-quark, 0)

---

### Post by TheFu on 2014-08-05
"automount" is an extremely specific term - it is confusing to see it here, since you don't really want to use that software.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) explains how to add a line to the fstab file - so that your other partition(s) will be mounted at boot time.
If you need more help/instructions, please ask.

---


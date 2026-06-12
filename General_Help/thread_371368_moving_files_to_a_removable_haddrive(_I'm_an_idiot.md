---
title: "moving files to a removable haddrive( I'm an idiot)"
date: 2007-02-26
forum: General Help
---

### Post by corytoneill on 2007-02-26
I am trying to move a folder to my usb harddrive, it says i don't have permission, can anyone help me?

---

### Post by cmost on 2007-02-26
What filesystem is the removable formatted with (i.e., FAT32, EXT3, NTFS...?)  If the filesystem is formatted with Windows' NTFS filesystem, then you'll need to install additional tools in order to write to it.  I highly discourage you from using a non-native filesystem with Linux.  If you've formatted the drive as EXT3 (recommended) then check to see which users have access to the mount point.  Sometimes, removable disks are set read only for users and world.  This can be changed by sudo chmod.  Finally, check /etc/fstab to ensure that the drive is setup to be 'rw' and not 'ro'.  Good luck!

---

### Post by corytoneill on 2007-02-26
i love the hoops that you have to jump through. haha

---

### Post by corytoneill on 2007-02-26
can you explain how to use the sudo chmod command, im an idiot

---

### Post by bodhi.zazen on 2007-02-26
What file system is on the usb ? ntfs, FAT, ext3 ???

---

### Post by corytoneill on 2007-02-26
how do i find that out???

---

### Post by bodhi.zazen on 2007-02-26
If you did not format the device is is likely fat32, possibly ntfs ..

Connect the usb device

Open a terminal,

Post the output of ```
sudo fdisk -l
```

---

### Post by corytoneill on 2007-02-26
it is ntfs, can you help me fix it

---

### Post by bodhi.zazen on 2007-02-26
Easiest way is with ntfs-config :

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by cmost on 2007-02-27
The easiest way is NOT necessarily with ntfs-config.  You should not use a non-native file system with Linux.  Writing to NTFS should be done rarely and only for purposes of interoperability.  Are you planning on sticking with Linux (Ubuntu) or are you just dabbling with the system?  If you are sticking with Linux, will you be using Windows also?  Will you use Windows more than Linux?  Is the external drive intended for backup purposes only or do you use it as one of your "regular" drives?

If you typically use Windows and you're only dabbling with Ubuntu to see what Linux is all about then I recommend you stick with NTFS on the drive and do what others have suggested and use ntfs-config (just don't be surprised later on down the road if something happens to your data - backup anything important first!)  If Linux is your main operating system, then reformat the external drive as EXT3 and then use EXT2IFS for Windows ([www.fs-driver.org)](www.fs-driver.org)).  This installs a pure kernel mode file system driver Ext2fs.sys, which actually extends the Windows operating system to include the Ext2 file system. Since it is executed on the same software layer at the Windows operating system core, all applications can access Ext2/3 volumes directly. Ext2/3 volumes get drive letters (for instance G:). Files, and directories of an Ext2/3 volume appear in file dialogs of all applications.  Since EXT2/3 is an open specification, reading and writing to it from Windows is much more reliable than reading and writing to NTFS, a closed file system, from Linux.

The best bay to reformat your external drive is from QTparted (or Gparted in Gnome)  You can install it from the repository.  Good luck!

---


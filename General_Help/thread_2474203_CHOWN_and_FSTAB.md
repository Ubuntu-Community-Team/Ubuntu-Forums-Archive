---
title: "CHOWN and FSTAB"
date: 2022-04-23
forum: General Help
---

### Post by Enigma12 on 2022-04-23
I found out when I first started using Linux over 8 years ago that, to access each of my hard drives' partitions, I needed to invoke CHOWN for each and have done so. I also have read about using FSTAB, and i have printed instructions on using both, but I have never invoked FSTAB. 

Does FSTAB require me to enter my password to access any hard drive partition, as CHOWN does? What, if anything, would I gain by also invoking FSTAB?

Thanks in advance for educating me on this matter.

---

### Post by mikewhatever on 2022-04-23
<fstab> is a configuration file to automount partitions. It can not be invoked.  You can check its contents with <less /etc/fstab>.

---

### Post by TheFu on 2022-04-23
/etc/fstab is a setting file that controls which file systems are mounted, where, with what options.  There are different required options based on the file system used.  fstab is NOT a command.

chown **is** a command.  It is only available in a useful way for accounts with sudo capabilities.  chown only works with file systems that support the POSIX standards - some examples of those commonly used are ext2, ext3, ext4, xfs, btrfs, zfs, f2fs, jfs, nfs, sshfs.

Note which file systems are NOT included - NTFS, FAT32, exFAT.  Those don't support chown or chmod because they aren't fully posix compliant, as far as Linux is concerned.  CIFS/samba is NOT posix compliant either, though those protocols can be used to share native file systems (and should) if NFS isn't a viable option.

So ... if you have a non-POSIX file system, like NTFS, and want it to be mounted with a non-root owner, then you'll need to setup the configuration in the fstab with the owner, group, and permissions to be used.  The problem with this is that all files and all directories get the permissions based on the fstab line for that file system mount. No deviation is possible. chown and chmod don't work.

My beste advice is to learn Unix file and directory permissions.  Spend the 45 minutes of concentrated effort. That's 15 minutes working through one of the 10 thousand online tutorials, and 30 minutes playing around with 3 different userids with 2 different groups. I'd use 3 different terminal windows for this - 1 terminal for each different "play" userid.  Create directories and files in a "play" directory under /tmp/foo/ ... see which permissions, groups, ownership allow and disallow access.  You'll learn there is a simple elegance to the Unix permissions. BTW, every popular OS uses these today, except 1.  All the others use it, so it isn't just for Ubuntu or Linux, but for OSX/MacOS and Android too. It is extremely useful knowledge.

After learning this, circle back around to see if the fstab makes a little more sense.  

A reference: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  ... it introduces users, groups, then permissions, since the order that concepts are introduced matters greatly.

---

### Post by oldos2er on 2022-04-24
/etc/fstab is a text configuration file, to change it you would open it in a text editor. Please make a backup copy of any system files before altering them.

---


---
title: "Unwanted desktop shortcut to NTFS partition on internal hard drive"
date: 2008-04-27
forum: General Help
---

### Post by Freelance Physicist on 2008-04-27
I'm dual-booting Windows and Ubuntu and I have an NTFS partition on the hard drive which I use for document storage shared between the two operating systems.  This is mounted as ~/Documents in Ubuntu.

After upgrading to 8.04, deleting files off the NTFS partition no longer results in moving the files to .Trash-$USER/ on the root directory of the partition, but instead presents a dialog box with options to delete immediately.  I thought this was odd behavior and installed ntfs-config thinking that there was some read/write permissions issue (even though I could do everything else with my files just fine).  After enabling write support for internal hard drives and remounting everything, I now have a shortcut to this partition on my desktop.

I want to restore the previous behavior of having a shortcut to this NTFS partition (mounted at ~/Documents) only in the Places menus.  I've changed /etc/fstab back to the way it was before ntfs-config made changes, but there is still a desktop shortcut to this partition after rebooting.

Relevant line from /etc/fstab:
```
# /dev/sda6
UUID=5A0914F10D6724C2    /home/mark/Documents    ntfs    defaults,umask=007,gid=46    0    1
```

Relevant line from output of 'mount':
```
/dev/sda6 on /home/mark/Documents type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
```

=========================================
Edit: Post #4 contains solution

---

### Post by bollix47 on 2008-04-27
Could [_this_]("http://ubuntuforums.org/showpost.php?p=4798693&postcount=3") be what you're searching for?

---

### Post by Freelance Physicist on 2008-04-27
Not quite, if I do that, then icons for flash drives and other external media devices no longer appear on the desktop, which I do want to happen.

Essentially, I want any drive mentioned in /etc/fstab to be treated like any other directory.  Another symptom is in the places menu (see attachment). Before, the icon for Documents was a folder like the ones for Downloads, Music, etc.  The second appearance of Documents with the same icon makes me think that Ubuntu is treating this partition as an external hard drive rather than an internal one, since this location is where links to flash and other external media appear.

---

### Post by Freelance Physicist on 2008-05-02
I solved this problem by editing my /etc/fstab file to mount my NTFS partition as /mnt/Documents instead of under my home directory.  This seems to be the proper way to deal with extra partitions.  To access my files as I used to, I created a symlink to that partition in my home directory.

---


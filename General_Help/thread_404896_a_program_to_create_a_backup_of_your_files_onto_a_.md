---
title: "a program to create a backup of your files onto a cd"
date: 2007-04-09
forum: General Help
---

### Post by Fittersman on 2007-04-09
i need to reinstall windows, and as far as i know there is no way to install it without losing ubuntu, so i was wondering if there is some program out there for ubuntu that will create an exact backup of your files.

because i have a custom theme and a custom bootsplash and a custom startup screen and login screen and stuff like that, i would rather not have to do all that again (mostly because i dont remember how i did it) so the program would need to make it as if i never had to reinstall and it would be exactally as it was before (it would need to save everything for all users too)

i could also settle for less i suppose :D

or i could back it up all manually maybe? somehow?

---

### Post by zvacet on 2007-04-09
You will not lose Ubuntu exept you overwrite it,but you will have problem with MBR.It can be solved.
[http://ubuntuforums.org/showthread.php?t=358183&highlight=grub]("http://ubuntuforums.org/showthread.php?t=358183&highlight=grub")
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub")

---

### Post by Fittersman on 2007-04-10
im going to need to completely format my drive though (low format), unless there is some way to format only the windows partitions?

---

### Post by tommcd on 2007-04-10
When you boot up the windows install disc it should see your partitions. Your windows partition will likely be the 1st one (assuming it is /dev/hda1 or /dev/sda1 in your fstab). The windows partition will be identified as ntfs, while the linux partitions wii likely be "unknown file system" or something like that. So just reformat the ntfs partition and install windows there and leave the other partitions alone.
You will have to reinstall grub though.
EDIT: See this to install grub from the live CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
or the alternate CD
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

---

### Post by Fittersman on 2007-04-10
so, that would low format the windows partitoin and leave my ubuntu one alone? cuz that would be cool i guess :D

---

### Post by mssever on 2007-04-11
If you're committed to backing up your entire system and you have some place to put the backup that's formatted with a Linux filesystem (such as ext2/3 or reiserfs), just do ```
cd /
cp -ar boot /path/to/destination
cp -ar bin /path/to/destination
``` etc. Omit /proc, /sys, and /dev. You probably want to omit /media and /mnt, as well.

Use cp -ar to restore. The -a flag to cp means to preserve everything (owner, permissions, special files, etc.). If you don't use -a, you'll end up with a horrendously broken system that will be extremely difficult to restore.

You can also create an optionally compressed tarball. I don't remember the exact command to use. *Be sure that whatever program you use preserves ownership, permissons, symlinks and special files, and so forth!*

EDIT: If you're copying onto a CD, cp -a won't work because the CD filesystem, ISO 9660, doesn't support everything a Linux filesystem does. A tarball will still work, though.

---

### Post by Fittersman on 2007-04-11
i would need to use a cd, because i dont have  a second hard drive.

whats a tarball do?

---

### Post by mssever on 2007-04-11
A tarball is an archive, similar to a zip file, but supporting Linux filesystem stuff. The command ```
cd /
tar -cjvf tmp/backup.tar.bz2 --exclude dev --exclude media --exclude mnt --exclude proc --exclude sys --exclude tmp *
```will likely do the trick, though I haven't tested it. For a short summary of the options for tar, type ```
tar --help | less
```More details are at ```
man tar
#or
info tar
```To restore, do either:
```
cd /
tar -xjvf /path/to/backup.tar.bz2
```or extract the tarball by double clicking its icon in Nautilus. Be sure to reboot after such a major operation (you'll be replacing running program files!).

---

### Post by Fittersman on 2007-04-11
just a question about the --exclude statements, why did you put them in there? (im assuming that --exclude media will exclude my media from the backup?)

i want to back up absolutely everything on my ubuntu partition, so could i take them out? (unless i assumed wrong of course)

sorry for all the questions and stuff, but i dont want to take any chances with this.

---

### Post by mssever on 2007-04-13
/media is where removable devices (CDs flash drives, external HDs, etc.) are mounted. There's no point in backing them up, because you already have a copy.

In Linux--and other UNIX variants--everything is a file. So your removable devices are represented as files, and we exclude their mountpoints, /media and /mnt, and the "files" that represent the actual devices, which are located under /dev (/dev actually contains files pointing to just about every phisical devices attached to your system, as well as to devices that exist only in software). /proc and /sys store representations of the current state of the system, so backing them up is just wasting space. Incidentally, You can see the contents of your system's RAM by reading /proc/kcore.

---


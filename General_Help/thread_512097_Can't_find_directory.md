---
title: "Can't find directory"
date: 2007-07-28
forum: General Help
---

### Post by methinks on 2007-07-28
Here's a new one (to me at least) which I hope can be fixed:
In my home folder, I have a directory called "media", where I keep all my images, videos, music, etc, which now seems to have disappeared. The link still shows up in my home folder, but when I click on it, what ever program is looking for it just searches without end. This also means that many of the problems that look for a directory at startup, such as Azureus, don't manage to load anymore.

Is there any way to fix the linking, or to run a hard drive recovery program?
I believe that the drive in question is partitioned as ext 2 or 3, I'm not sure.

Any help would be appreciated.

---

### Post by fragos on 2007-07-28
/media is already used by Linux when mounting storage.  Your problem may be in your dual use of that directory.  I'd choose another name.

---

### Post by methinks on 2007-07-28
that's not it... It's been working for months, the error just occurred this morning.

The /media that you mean is right on the root, I've got my missing directory under my /home.

---

### Post by meierfra on 2007-07-28
We need some more information:

It sounds like your are mounting a partition to your folder "media". If yes, post the output of
```
 gedit /etc/fstab 
```

and 

```
sudo fdisk -l
```

---

### Post by methinks on 2007-07-28
meierfra: If I understand you correctly, then no I'm not mounting a partition under "media"

In my "home" folder, I have several directories: projects, downloads, media.
So the "media" folder in question, (/home/alex/media) has nothing to do with the (/media) folder. The fact that they have the same name is a coincidence, which I didn't notice until after I had my directories set up. (I'm a noob at linux, otherwise I probably would have done it differently.)

So the folder in question is just a directory on the main file system, not a separate partition.

That said, here is the info you asked for:
fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=dd966421-2746-40e5-ade4-5d786daca765 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=d96ea733-c479-4c21-8dc8-e19d5039d8a5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

And fdisk
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37589   301933611   83  Linux
/dev/sdb2           37590       38913    10635030    5  Extended
/dev/sdb5           37590       38913    10634998+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by meierfra on 2007-07-29
Sorry, wrong guess. So also the information you gave me is not of much use. (Allthough I'm curious: according to your  fdisk output you have 3 different 320 gig hard drive, but only of them is mounted. What are you using the other two for?)

How many  files are in "media" and that is the total size (To find out : right-click on  "media"  and  select properties)

---

### Post by methinks on 2007-07-29
The other two drives are my windows partition, and one blank drive that I was originally going to set up as raid, (which didn't work) and which is now sitting empty. I was going to move my home directory onto it, to make it a pure data drive, (and to share it between OS's) I just haven't got around to it yet.

---

### Post by rillip on 2007-07-29
How about your /etc/mtab?  I don't see any hdd's mounted at all, though it looks like maybe two sata drive are mounted in a way I don't understand

---

### Post by meierfra on 2007-07-29
can you access "media" from the terminal?

For example, what happens if you type


```
  ls -l media 
```

(l is a lower case L,
this should list all the files and folders in "media")

or 

```
  cd media 
```

---

### Post by kyphi on 2007-07-29
How frustrating.  A whole directory with all your music and pictures gone.

1.  In Linux you cannot delete a directory unless it is empty.
2.  In Linux, once you delete something it is not retrievable.

Have you tried, under your Places menu, your search facility?  Look for the 'media' folder and also, if you can remember the names of any of the files in your media directory.

Another thing to try is to right click the link to the media folder in your home directory and see what it says there.
Perhaps the path to the folder has become corrupted.

You might also like to enable 'View Hidden Files' in your home directory and see if you can find anything.

You can also try to create a folder in your home directory called 'media' to see if you can get a message that says: this file already exists.

Do those things first before we go further, please.

---

### Post by meierfra on 2007-07-29
kyphi:  I think the first post  says that "media" is still in the home folder. But it cannot be opened. Maybe there are   more files in it than the computer can handle.

---

### Post by fragos on 2007-07-29
Have you considered that you may have inadvertantly moved the folder.  Open a terminal window and type "locate media".  This will identify where any occurance of media is located.

---

### Post by fjgaude on 2007-07-29
Hey, are you sure you have the drive mounted that /home/alex/media is on? From the looks of your fstab it isn't mounted. From command line type "mount" and see what it says. I don't think you'll find the drive where all your music is on mounted.

Did you link /media to /alex? You know like using the command ln to link one directory to another? A command like:

sudo ln --symbolic -T /home/alex/media media     with media being on another drive, like sdc1?

frank

---

### Post by rillip on 2007-07-29
> **kyphi said:**
> How frustrating.  A whole directory with all your music and pictures gone.

1.  In Linux you cannot delete a directory unless it is empty.
2.  In Linux, once you delete something it is not retrievable.


This is quite incorrect.  It simply moves it to the folder's .Trash folder, which is hidden.  You can restore it.  Gnome doesn't have a trashcan icon to restore from for some stupid reason, but KDE and XFCE both do.  File deleteion works identically to Windows almost.  For example, I just deleted a file and ran the command locate for it.  It is found now in /home/peatheri/.local/share/Trash/files

---

### Post by fjgaude on 2007-07-29
> **rillip said:**
> This is quite incorrect.  It simply moves it to the folder's .Trash folder, which is hidden.  You can restore it.  Gnome doesn't have a trashcan icon to restore from for some stupid reason, but KDE and XFCE both do.  File deleteion works identically to Windows almost.  For example, I just deleted a file and ran the command locate for it.  It is found now in /home/peatheri/.local/share/Trash/files

While we are at it, you can delete a directory, full or not:

sudo rm -d -r /dir

The -r takes care of any files recursively and deletes them. There can be many subdirectories.

rmdir removes only empty directories, yes, but rm can remove them when they have undeleted files.

Try "man rm" for all the options.

With gnome, the trashcan is in the panel. Left click and the so-called deleted files show. From there you can drag and down them to where you wish to have them restored, one at a time, a grouping, or all of them.

frank

---

### Post by fragos on 2007-07-29
> **rillip said:**
> This is quite incorrect.  It simply moves it to the folder's .Trash folder, which is hidden.  You can restore it.  Gnome doesn't have a trashcan icon to restore from for some stupid reason, but KDE and XFCE both do.  File deleteion works identically to Windows almost.  For example, I just deleted a file and ran the command locate for it.  It is found now in /home/peatheri/.local/share/Trash/files

In a clean install the trash can icon is at the end of the lower icon bar.  It will be trash for the logged in user.  Root user has it's own trash can.  If you right click the applet bar and select "Add to panel" you can add a trash can.

---

### Post by kyphi on 2007-07-29
As in Windows, deleted items go into the garbage bin.  If you delete them from the bin they are gone.

In Windows you can still retrieve files after they have been deleted from the bin most of the time but in Linux, once deleted from the garbage bin, the file is gone (the garbage bin is linked to the .Trash folder).

As to deleting recursively, yes that is correct but I doubt that this information would help methinks, the originator of this post, nor would it lift his spirits after such a disaster.

---

### Post by methinks on 2007-07-29
Well, I just tried to access the directory via the terminal, and this is what it gave me:
```
alex@cruft:~$ cd media
alex@cruft:~/media$ dir
Segmentation fault
alex@cruft:~/media$ 
Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] Assertion failure in dx_probe() at fs/ext3/namei.c:384: "dx_get_limit(entries) == dx_root_limit(dir, root->info.info_length)"

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] ------------[ cut here ]------------

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] invalid opcode: 0000 [#1]

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] SMP 

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] CPU:    0

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] EIP:    0060:[<f8a17b51>]    Tainted: P      VLI

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] EFLAGS: 00210286   (2.6.20-16-generic #2)

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] EIP is at dx_probe+0x1e1/0x320 [ext3]

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] eax: 00000090   ebx: f7372000   ecx: 00200082   edx: 00000000

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] esi: f7372018   edi: f694ae10   ebp: f79f3114   esp: f691be40

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] Process dir (pid: 6353, ti=f691a000 task=c3237a90 task.ti=f691a000)

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] Stack: f8a23f28 f8a2326b f8a25d6d 00000180 f8a24078 f691bea8 00000000 00000003 

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]        00000000 f7399660 00000000 00000000 f79f3114 f8a18edd f691be90 f691bebc 

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]        fffab000 00000000 00000000 f68ef540 00000000 00000000 000280d2 c03aafac 

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] Call Trace:

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [<f8a18edd>] ext3_htree_fill_tree+0xad/0x200 [ext3]

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [<f8a11062>] ext3_readdir+0x112/0x640 [ext3]

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [kmap_atomic+134/160] kmap_atomic+0x86/0xa0

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [kunmap_atomic+107/112] kunmap_atomic+0x6b/0x70

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [filldir64+0/224] filldir64+0x0/0xe0

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [filldir64+0/224] filldir64+0x0/0xe0

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [vfs_readdir+148/176] vfs_readdir+0x94/0xb0

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [sys_getdents64+111/192] sys_getdents64+0x6f/0xc0

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  =======================

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] Code: 44 24 10 78 40 a2 f8 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d 5d a2 f8 c7 44 24 04 6b 32 a2 f8 c7 04 24 28 3f a2 f8 e8 bf f0 70 c7 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 40 a2 f8 c7 44 24 04 6b 

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000] EIP: [<f8a17b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:f691be40

Message from syslogd@cruft at Sun Jul 29 16:19:16 2007 ...
cruft kernel: [  239.604000]  [<f8a22610>] ext3_permission+0x0/0x10 [ext3]

```

If it makes any difference, I do access this drive from windows (I think I use the EXT32IFS driver)

---

### Post by kyphi on 2007-07-29
Segmentation fault is a system error and could well be caused by the folder bursting at the brim as suggested by meierfra.

If you can access this folder from Windows, can you transfer the most recently added file to another folder? or delete a large file that you no longer want to keep.

Fingers crossed.

---

### Post by meierfra on 2007-07-29
I searched google for your error message

> Assertion failure in dx_probe() at fs/ext3/namei.c:384

and found various links. It seems that your file system got corrupted. Maybe by accessing it from Windows.
But it seems to be fixable. Here is one  of the links  I found:

[https://bugs.launchpad.net/linux/+bug/109177]("https://bugs.launchpad.net/linux/+bug/109177")

---

### Post by methinks on 2007-07-29
I can't actually access the file system in windows either, otherwise I would try deleting a chunk of stuff...

Does anybody know how to start an HDD integrity check, like what happens every 30 boots? I thought that might fix it.
Also,  the linked article mentioned rebuilding the directory index, how do you do that?

---

### Post by meierfra on 2007-07-29
> Does anybody know how to start an HDD integrity check, like what happens every 30 boots? 

According to the linked article, do this:

```
tune2fs -O ^dir_index
```
(This  slows down  the disk check. I guess its necessary since your file system got corrupted)

```
sudo touch /forcefsck 
```

This causes a disk check during the next boot-up.

---

### Post by methinks on 2007-07-30
running fsck seems to have fixed it.

Thanks for all the help!

---


---
title: "Unable to delete directories in Trash"
date: 2007-07-08
forum: General Help
---

### Post by mfrauenstein on 2007-07-08
I was cleaning up my Music directory and somehow ended up with 2 directories in Trash that will not delete or be removed because of ????? I select the option to empty trash but they stay. Funny thing is that the system does not see them as directories but files! How would I get to Trash on the command line to clear Trash manually. 
PS. On Feisty 7.04 using Gnome

---

### Post by AlexThomson_NZ on 2007-07-08
cd ~/.Trash
rm -rf *

---

### Post by aysiu on 2007-07-08
Alt-F2 ```
gksudo nautilus
``` Press Control-L and type ```
 /home/*username*/.Trash
``` and hit Enter. Go to Edit > Preferences > Behavior > Trash and check *Include a Delete command that bypasses the Trash*.

Finally, right-click the folder you want to delete and select *Delete*

This is the safest delete method. 


Do not **ever** type or paste ```
sudo rm -rf /home/*username*/.Trash/*
``` in the terminal, no matter what anyone tells you.

---

### Post by AlexThomson_NZ on 2007-07-08
> **aysiu said:**
> Do not **ever** type or paste ```
sudo rm -rf /home/*username*/.Trash/*
``` in the terminal, no matter what anyone tells you.

To be fair he asked how to clear the Trash folder *on the command line*, and I tried the command I suggested myself before I suggested it to him.

Is there an issue with this way I don't know about?

---

### Post by southernman on 2007-07-09
> **AlexThomson_NZ said:**
> To be fair he asked how to clear the Trash folder *on the command line*, and I tried the command I suggested myself before I suggested it to him.

Is there an issue with this way I don't know about?IMO the only issue would be simple a typo, either from the person writing it, or end user entering it.

---

### Post by AlexThomson_NZ on 2007-07-09
That's what I thought (and that's why you wouldn't do it as root).

---

### Post by aysiu on 2007-07-09
Well, the problem is that if it's a folder that can't be emptied from the trash, you probably would have to delete it as root.

There is nothing technically speaking that's wrong with using *sudo rm -rf ~/.Trash*, but, as southernman hints at, there could be user error. I'm thinking specifically of hitting the Enter key too soon by accident.

---

### Post by AlexThomson_NZ on 2007-07-09
My logic behind not suggesting to do it as 'su' is that in this case I don't think this is the reason why he can't delete the file.

I think the problem is a broken inode on the filesystem, which is why it appears as a file rather than a directory.

---

### Post by aysiu on 2007-07-09
> **AlexThomson_NZ said:**
> My logic behind not suggesting to do it as 'su' is that in this case I don't think this is the reason why he can't delete the file.

I think the problem is a broken inode on the filesystem, which is why it appears as a file rather than a directory.
You may be right on that count.

Guess we'll have to hear back from the OP first.

---

### Post by mfrauenstein on 2007-07-09
Thanx for the suggestion. I did as requested in the safest method. Nothing happens. Entries remain. Is there a log of sorts I can check? Thank you for the help so far.

---

### Post by mfrauenstein on 2007-07-09
Then I tried the following after re-reading all posts.
============
martin@tsdlap1:~$ cd ~/.Trash
[email]martin@tsdlap1:~/.Tras[/email]h$ rm -rf *
rm: cannot lstat `Simon & Garfunkel': Permission denied
rm: cannot lstat `Various': Permission denied
[email]martin@tsdlap1:~/.Tras[/email]h$ su
Password: 
[email]root@tsdlap1:/home/martin/.Tras[/email]h# rm -rf *
rm: cannot lstat `Simon & Garfunkel': Permission denied
rm: cannot lstat `Various': Permission denied
[email]root@tsdlap1:/home/martin/.Tras[/email]h# 
=============

Does that help any?

---

### Post by aysiu on 2007-07-09
That's baffling.

Some in the GUI as root it can't be deleted.

And in the terminal as root it can't be deleted.

How can that be?

---

### Post by Bothered on 2007-07-09
Is the trash directory on a partition mounted as read only (unlikely, but I can't think why the delete command didn't work)? Are the two files owned by root and marked as read only for the owner?

---

### Post by AlexThomson_NZ on 2007-07-09
Can you post the output of:
ls -l ~/.Trash

Like Bothered said though, how could files appear in the user's trash if they are only readable by root?

Hopefully it is just a permission/owner thing- the alternative is fsck I guess- and if I can't tell you to rm files from the command-line, no way am I going to tell you how to use that! :)

---

### Post by mfrauenstein on 2007-07-09
Thanx again, here is the output requested from 

ls -l ~/.Trash

=========
martin@tsdlap1:~$ ls -l ~/.Trash
total 0
?--------- ? ? ? ?                ? /home/martin/.Trash/Simon & Garfunkel
?--------- ? ? ? ?                ? /home/martin/.Trash/Various
martin@tsdlap1:~$

---

### Post by AlexThomson_NZ on 2007-07-09
yikes!

man fsck

Good luck! :D

---

### Post by Bothered on 2007-07-09
Could you also post the result of:

sudo fdisk -l

and of:

cat /etc/fstab

---

### Post by mfrauenstein on 2007-07-09
As requested 
===============
martin@tsdlap1:~$ sudo fdisk -l
Password:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         383     3076416   12  Compaq diagnostics
/dev/hda2   *         384        6247    47102580    c  W95 FAT32 (LBA)
/dev/hda3            6248       12161    47504205    f  W95 Ext'd (LBA)
/dev/hda5            6248        8797    20482843+   b  W95 FAT32
/dev/hda6           11985       12161     1421721   82  Linux swap / Solaris
/dev/hda7            8798       11984    25599546   83  Linux

Partition table entries are not in disk order
=====================
martin@tsdlap1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=094c6af9-1665-40a5-b1c0-ca5920446b11 /               reiserfs notail          0       1
# /dev/hda1
# /dev/hda2
# /dev/hda5
# /dev/hda6
UUID=5ee51998-95e4-44f5-9c80-a640c692eecb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

# Generated by Automatix
/dev/hda2   /media/hda2   vfat    iocharset=utf8,umask=000  0    0
/dev/hda5   /media/hda5   vfat    iocharset=utf8,umask=000  0    0
## End of Automatix mounted partitions
============
Thanx again.

---


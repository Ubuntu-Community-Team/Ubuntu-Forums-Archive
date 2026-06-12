---
title: "System booting into emergency mode/&quot;structure needs cleaning&quot;"
date: 2022-07-08
forum: General Help
---

### Post by bat-flattery on 2022-07-08
Hi all,

I'm getting emergency mode when booting up my 18.04 installation.  It's an old installation that I've had for about 4 years.  The OS is installed on a SSD and my home folders are on a HD.  The SSD appears to be fine, and when booting up from a live CD, I can access one user folder, but my main user folder gives the following error message:

"This location could not be displayed. Sorry, could not display all the contents of "thomas": Error when getting information for file "media/ubuntu/f9848184-088c-495d-b29c-bf2342248bb3/thomas/.cinnamon": Structure needs cleaning"

I have tried the gnome disk tool, which gives the following error while disk checking:

"Error checking filesystem on /dev/sdb3: Process reported exit code 12: e2fsck 1.44.1 (24-Mar-2018) 
ext2fs_read_inode: Inode checksum does not match inode while reading inode 5087289 in process_bad_inode
e2fsck: aborted 
(udisks-error-quark, 0)"

Have also tried fsck -p, and got the following error:

```

ubuntu@ubuntu:~$ sudo fsck -p /dev/sdb3
fsck from util-linux 2.31.1
/dev/sdb3 contains a file system with errors, check forced.
/dev/sdb3: Inodes that were part of a corrupted orphan linked list found.  

/dev/sdb3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
```


I did some googling on these errors but the answers are either beyond my comprehension, or they seem to imply that this disk is severely damaged and requires expert recovery.  Sounds to me like my disk is gone.  Anything else I should attempt before wiping the entire installation?  In your answer please take into account that I'm a normal person who can use a computer fine but I don't really know what I'm doing in the terminal or when I'm fiddling about with drive structures.  I can follow instructions but please don't assume I know what I'm doing. 

Thanks for any help! :P

---

### Post by tea for one on 2022-07-08
> **bat-flattery said:**
> 
Have also tried fsck -p, and got the following error:
```

ubuntu@ubuntu:~$ sudo fsck -p /dev/sdb3
fsck from util-linux 2.31.1
/dev/sdb3 contains a file system with errors, check forced.
/dev/sdb3: Inodes that were part of a corrupted orphan linked list found.  

/dev/sdb3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
```
First priority is to [COLOR="#0000FF"]backup[/COLOR] your data if you have not already done so.
Have you tried to run fsck manually?

Boot into a live session and open a terminal.
[COLOR="#0000FF"]Identify[/COLOR] the partition number - previously reported as sdb3.
```
sudo fsck /dev/sdb3
```

---

### Post by bat-flattery on 2022-07-11
Thank you! I thought a manual scan was going to be far beyond my ability.  It sort of was, as it asked a lot of questions I didn't know the answer to. My solution was just to answer 'yes' to everything.  At one stage I actually put a rock down on the Y key so it would stop bugging me!

Anyway, 90% of my data is back.  Thank you!  The drive even boots, although some functionality is missing.  Is there any way for me to know if this drive is physically ok?  As in, how do I know if it's new computer time, or if I can just reinstall?

---

### Post by Quarkrad on 2022-07-11
You could run a SMART test on your SSD - there are many web pages that will tell you how to do this using ubuntu.  I would then power down and disconnect every piece of h/w and re-connect it - faulty connections can lead you up all sorts of paths and waste a lot of time (pc inners may need a 'hoover' as well).  Once you have all your data off consider upgrading to something like 22.04 - the latest LTS.

---


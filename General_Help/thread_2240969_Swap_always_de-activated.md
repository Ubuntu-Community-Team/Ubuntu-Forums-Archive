---
title: "Swap always de-activated?"
date: 2014-08-23
forum: General Help
---

### Post by Mike_Walsh on 2014-08-23
Afternoon, all.

I appear to have a small problem with my Ubuntu 14.04 LTS installation.

I've noticed, over the last 2 to 3 weeks, that whenever I check the System Monitor, the swap partition is always 'unavailable'. Upon checking in GParted, and right-clicking the swap partition, the option for 'swapon' is always there (i.e., not greyed-out). Thus, it always gets turned on, and away I go. Until the next time it happens.....

Does anybody happen to have any suggestions as to why this is happening? And, more to the point, how I can stop it from doing so?

Any information would be appreciated.

Regards,

Mike.

---

### Post by ajgreeny on 2014-08-23
For some reason it appears that your /etc/fstab file is incorrectly pointing to the swap partition but it should be a simple edit to put right.

Let's see the output of ```
sudo blkid -c /dev/null
cat /etc/fstab
```

---

### Post by Mike_Walsh on 2014-08-23
Hi, AJ.

Okay; output of sudo blkid -c /dev/null is as follows:-

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ sudo blkid -c /dev/null
[sudo] password for paul: 
/dev/sda1: UUID="ec7eb204-1006-411f-8b8d-e8285c0c9e20" TYPE="ext4" 
/dev/sda5: UUID="46cb8f62-e9ef-45a1-a2c0-3595b07a0b0b" TYPE="ext4" 
/dev/sda6: UUID="44ddc7e2-77bd-4731-b0be-2030c6a5f98e" TYPE="swap" 
/dev/sdb1: LABEL="Seagate #1" UUID="5844629444627522" TYPE="ntfs" 
/dev/sdb3: UUID="f28d25eb-62b4-429d-9b28-b43f1cdef1e1" TYPE="ext4" 
/dev/sdb5: UUID="2040a712-81a8-4e76-804e-9b1c9416be5a" TYPE="ext4" 
/dev/sdb6: UUID="2ad00ca8-6c50-400e-aff2-2c3debbf9843" TYPE="ext4" 
/dev/sdb7: UUID="a27a03bb-6e39-40fd-b668-a0e5e1233559" TYPE="ext4" 
/dev/sdb8: UUID="db2661de-5639-4d6a-ad65-b85311cf2dfa" TYPE="ext4" 
/dev/sdb9: UUID="16bec422-bb20-441a-84dd-510ac25bebff" TYPE="ext4" 
/dev/sdb10: UUID="d97bc690-6d5f-47c4-a248-65112ed13c49" TYPE="swap" 
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 


And cat etc/fstab is as follows:-

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=ec7eb204-1006-411f-8b8d-e8285c0c9e20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2f40eb9c-3c0e-46f3-98e4-d18b74530e9f none            swap    sw              0       0
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 


Is that what you need? It appears that the swap wasn't on during the primary installation. Sda5 is my Zorin installation; I forget now exactly how I DID do it.....Zorin's OS 9 was installed about 6 weeks ago.

I can send you a screenshot from GParted if required.

Regards,

Mike.

---

### Post by Bashing-om on 2014-08-23
Mike_Walsh; Yepper !

ajgreeny has the right of it !
> 
/dev/sda6: UUID="44ddc7e2-77bd-4731-b0be-2030c6a5f98e" TYPE="swap" 

 swap was on /dev/[color=red]sda5[/color] during installation
UUID=2f40eb9c-3c0e-46f3-98e4-d18b74530e9f none swap sw 0 0
BK
/dev/sdb10: UUID="d97bc690-6d5f-47c4-a248-65112ed13c49" TYPE="swap" 
##only 1 swap partition is required, you may safely delete this one after making the changes##


Make the changes in the /etc/fstab files(s) for what 'blkid' relates.

[INDENT][INDENT]workie great
[INDENT][INDENT][INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-08-23
Hi, Bashing-om.

Okay; I hate to be such a noob over this (I'm learning new stuff every day in Ubuntu!)... What precisely requires editing? In other words, what am I looking to end up with?

I have NEVER been afraid to ask for help, when I don't know something. ;)

Regards,

Mike.

---

### Post by ajgreeny on 2014-08-23
Edit your /etc/fstab file (as root) with ```
sudo nano -B /etc/fstab
```and change the line 
```
UUID=2f40eb9c-3c0e-46f3-98e4-d18b74530e9f none            swap    sw              0       0
```
to read
```
UUID=2040a712-81a8-4e76-804e-9b1c9416be5a none            swap    sw              0       0
```
then run ```
sudo mount -a
```and if no error message appears you should be good to go.

EDIT:
It has occurred to me a bit late that you may not know how to use nano, the command line text editor.

Navigate with cursor keys to the line and position needed and make the changes needed as in any text editor, though you will not be able to use the mouse as in a GUI editor.  Once you have made the changes use Ctrl+O (letter O, not zero) to save, hit enter to accept the file name (you will see it offered as file name at the bottom) then Ctrl+X to exit nano. The -B option will make a backup when you save the file, which is a good thing to do, just in case.

---

### Post by Mike_Walsh on 2014-08-23
Hi again, AJ.

Sorry to be a while getting back to you; some of the family came round for a while, and.....well, you know how THAT goes!

Have applied your fix, and no error message has come up, so I assume I'm sorted?

BTW, I believe it was you who was explaining to me about using nano a few weeks ago, so I remembered how things worked from that session. Anyway, I've done a restart, and checked in GParted, and the swap now appears to be on, as it should be.

Thanks for that nugget of information; another trick to file away in my 'little black book'!

Another one to mark as 'Solved'...

Appreciated.

Regards,

Mike.

---

### Post by ajgreeny on 2014-08-24
Great!

You can check the swap situation with command **free -m** which will give you info like this
```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7682       2210       5471          0        147       1155
-/+ buffers/cache:        907       6774
Swap:         8198          0       8198
``` the bottom line shows the total swap, how much is used, and how much free.

---


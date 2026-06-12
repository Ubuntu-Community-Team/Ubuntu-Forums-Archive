---
title: "install error, login problems.. well.. HELP"
date: 2005-11-01
forum: General Help
---

### Post by KingGuru on 2005-11-01
first.
When I install, I get the following msg:
system~1_resto~1RP4sA0024647.exe is 4123K,  but it has 289 clusters (9248K)

Error!!!
..
if I ignore this, I can install the system, but when I get to the login screen, when I type my user, and pass, I get that I don't have 644 rights, ..
And after that it tells me, something about,
the last session lasted less than 10 seconds...

WEll..  this is my first time using ubuntu, and honestly.. I'm not impressed :( 

anyone know what to do with all this??

KingGuru

---

### Post by KingGuru on 2005-11-01
in the "last session.." part, it says
Could not set mode 0700 on private per-user gnome configuration directory '/home/user/.gnome2_private' : operation not permitted

soo.. 
I'm kinda more used to RH/fedora..
how do I get root acces.. I can't set root password in the install..
and if I type su- and use either my pass for my user, type nothing, root, admin, or what ever I could guess, it says authentication failed
how do I get that acces ?

-Kingguru

---

### Post by felix_stegerman on 2005-11-01
You don't usually have root account w/ ubuntu.
You use sudo to call other programs as root. (man sudo will tell you more)
If you really want root, you can (temporarily) enable the root user,
or just use "sudo -H bash" to open a root shell.

And when did you get that error? did you resize a windows partition?
It sounds like you have a bad install, you could try reinstalling.


Felix

---

### Post by KingGuru on 2005-11-02
Well..
The first error I get in the begenning after choosing partitions.
I have reinstalled a couple of times.. and actually used 2 diffrent cd's (same image, though), to test if it was a cd fault.

The other 2 errors I get when I get to the login picture (gui)
I can still log in in a terminal, but I serious don't know what to do there atm. I'm quite new to linux, and specially ubuntu

KingGuru

---

### Post by KingGuru on 2005-11-02
noone ?
damm.. I can't use ubuntu until anyonw knows what to do.. :(

---

### Post by felix_stegerman on 2005-11-02
Hi,

Is my assumption that you are dual-booting correct?
How did you partition?
What partitions do you have and what file systems do they use?


Felix

---

### Post by KingGuru on 2005-11-02
I have 2 disks in my current system.

I have my primayr disk 80 gig, with a 20 gig primary (windowsXP, ntfs), and on the extended I have a /home on 2.2 gig, a small /boot, a 2 gig swap, and a 15 gig system disk ( / ) .. all ext3 except the swap, that is linux swap system.
rest of the disk is ntfs

KingGuru.. 
thanks for the concern

---

### Post by felix_stegerman on 2005-11-02
Hi,

I think you may have a problem w/ partitioning or something, but
let's try to cover some other bases.

You may want to check the integrity of the CD image by getting the md5sums
file from the ubuntu download site and compare it to the output of running
an md5 checksum utility on the disk image you have.

With google, I found the following reference to creating md5 checksums on
Windows: [http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)

And I don't know whether this is useful, but:
Have you used the live CD? If so, did you have any problems with that?
If not, could you try that ...

Also, you did not answer my question whether you resized a windows
partition.


Felix

---

### Post by Gezzer on 2005-11-02
when u set the partitions up did u make them primary partitions or logical partitions on the space u freed up for the install of ubuntu ...

---

### Post by KingGuru on 2005-11-02
Well.. I just used my old Fedora Core 4 partitions.. formattet them, though.
sat them up using PQ magic several months ago.
My windows is on ptimary, .. all linux, and the extra ntfs space is on extended
I haven't tried live cd.. I'll just dl that now..
thanks for the help

KingGuru

---

### Post by KingGuru on 2005-11-07
Well..
I'm inside with live ubuntu. 
so.. what do I do now ?
remove all the linux partitions, and make them again, and try again ?

The same partitions worked just fine with fedora core 3/4

KingGuru

---

### Post by ScottEllis24 on 2005-11-07
you could try to format the HD's before installing ubuntu

---

### Post by felix_stegerman on 2005-11-07
[QUOTE=KingGuru]
When I install, I get the following msg:
system~1_resto~1RP4sA0024647.exe is 4123K, but it has 289 clusters (9248K)
[/QUOTE]

[QUOTE=KingGuru]
Well.. I'm inside with live ubuntu. so.. what do I do now ?
remove all the linux partitions, and make them again, and try again ?
[/QUOTE]

You should try that first.

If that does not work, I would recommend that you repartition your
entire hard drive, which also means you will have to reinstall windows.
The error message you got seems to suggest there is something wrong
with the partitioning, including the Windows part.
I'm not sure about all this, but it seems the most logical thing to be wrong.

Just reinstall windows. During installation, remove all partitions and then create a new windows partition. Then after windows is installed, reinstall
Ubuntu onto the remaining free disk space.

As I've said, I don't know whether this will help, but it seems like the most
logical thing to do. It's what I would do in your position.

And oh, REMEMBER TO BACKUP ALL YOUR IMPORTANT DATA BEFOREHAND.


Felix


P.S.
I wasn't entirely thuthful about doing exactly the same thing.
I personally wouldn't reinstall Windows ;-)

---

### Post by KingGuru on 2005-11-08
Well.. I'll get on to it.
Atm my hd is partitioned up as following
Primary:
20 Gb NTFS (for winblows)
Logical:
1 Gb linux Swap (I just upgraded from 512 -> 1.5 Gb in the machine, so this I might change in size)
25 Mb /boot partition
2 Gb /Home partition
13 Gb / partition
40 Gb NTFS (how is Ubuntu's support for ntfs ..  [http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/) haven't for debian/ubuntu as far as I can see)

Any surgestion (apart from removing my windows partition (need it for gaming)) ?
KingGuru

---

### Post by felix_stegerman on 2005-11-09
[QUOTE=KingGuru]Any suggestion?[/QUOTE]

When I get home (I'm @ university now), I'll post my partitioning scheme...

As for NTFS, I would suggest you use FAT to share files between Ubuntu & Windows.
AFAIK (reliable) NTFS write support is unavialabe, but reading from NTFS should work fine.


Felix

---

### Post by KingGuru on 2005-11-09
super.. I'll change it in the tomorrow.. (have a concert tonight)

---

### Post by ringding on 2005-11-20
Try something similar to this....

[http://www.ubuntuforums.org/showthread.php?t=80599](http://www.ubuntuforums.org/showthread.php?t=80599)

---


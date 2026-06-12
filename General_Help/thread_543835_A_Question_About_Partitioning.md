---
title: "A Question About Partitioning"
date: 2007-09-05
forum: General Help
---

### Post by Straylit Me on 2007-09-05
So ive got an 80gb hard drive. I planned on doing the follow but need some advice:

35gb - Windows
25gb - Fat32 Filesystem for music/video so linux and windows can both read and write to it.
23gb - / Ubuntu
2gb - swap

My question is regarding the fat32 partition. As far as installing games, loading it with music/video's, will Linux and Windows be able to use the partition without any (unknown to me) problems? Im trying to avoid having to have duplicates of every music/video file on each of the OS's and thought it would be easier if the two OS's could just share a partition.

---

### Post by kellemes on 2007-09-05
Yep, FAT32 is supported on both OS's.
Still.. ext3 is the better choice, there are excellent ext3-drivers for Windows (google will tell how to find and install them) and you get a better FS in return.
But FAT32 is fine too.. Just remember it has a 4Gb filesize limit. So a 4.22Gb movie will not fit.

---

### Post by Straylit Me on 2007-09-06
Thank you very much. I didnt think about the 4gb filesize limit. Perhaps ill just use ext3 then. Once again, thanks.

---

### Post by Luke771 on 2007-09-06
You don't really need FAT32, use Ex2/3 instead and install an ext* driver for Windows, one is at [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

My partitioning:
sda1 200MB Etx3 primary  /boot
sda2 10GB NTFS primary Windows
sda3 10GB Ext3 primary /
sda5 474.8GB ext3 logical /sda5 (linux), D: (win)
sda6 5GB logical,  swap

You could also mount sda5 as /home but I prefer not to mix up, so if I need to reinstall Linux there won't be a mess of /home stuff left in sda5.
Instead, I use symlinks to the most used directories in /home.
To make /sda5 writeable as regular user, use chown <username> /sda5 -R (chown = change owner, -R recursive: all the dubdirectories and filres too).
Files and directories created under windows will be owned by your user in linux because that's the owner of the whole directory.
I use one big partition for both file storage and win games install, another solution could be to make two storage partitions, one for pure storage in Ext*, accessible by both lin&win, and another in NTFS to install win. games into.

The idea of having small dedicated partitions for the OS's and everything else in a separate big partition accessible by both comes from the need of being able to reinstall any of the two OS's without losing data; I tend to make a mess of my OS's experimeting with them, but it's a cool solution even if you dont, for instance, say you get a virus, you reinstall windows and your data is still there, an Ubuntu upgrade fails and reinstalling is much easier than fixing it, reinstall and lose nothing. Etc.

Anyways. I have this tendency to make my posts unnecessarily long: the point was use Ext2/3 instead of FAT32, and make it accessible from windows with [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)
Also, use small partitions for the OS's and save everything on the common storage partition.

[edit: suggestion]
For an 80GB drive, I'd suggest

part: 1, 200MB /boot (primary) Ext3
part 2 8GB win (primary) NTFS
part 3 8GB ubuntu (primary) Ext3
part 4 ~56GB common storage (logical) Ext3
part 5 2.5GB swap (logical)

---

### Post by aquavitae on 2007-09-06
I agree with everyone recommending ext3, but remember you can also write to NTFS from ubuntu, so that is another option.  I'm not advocating it - I do think ext3 is better - but it is an option.

---

### Post by Luke771 on 2007-09-06
I've also read that you can write NTFS from Linux now, anyways, I still prefer not to.
OTOH, Windows does write pretty well on Ext3 with the installable driver, I've been using that for years and never got a problem, while Linux-on-NTFS is still relatively new and I haven't heard much about how good it is yet, so for now,  I think itìs better to stick with ext3

---

### Post by aquavitae on 2007-09-06
ext3 is nicer anyway :D

---

### Post by Mukaeutsu on 2007-09-06
>  For an 80GB drive, I'd suggest

part: 1, 200MB /boot (primary) Ext3
part 2 8GB win (primary) NTFS
part 3 8GB ubuntu (primary) Ext3
part 4 ~56GB common storage (logical) Ext3
part 5 2.5GB swap (logical)

as a question, at this moment i am reformatting to this setup, i saw it and said "wow, exactly what i had in mind!"
the only problem is that i am fairly new to linux, and do not know how to set this up, i am using the partitioner now

do i make p.1 200 MB EXT3 with a MOUNT POINT: "/boot" or what?

thanks a ton, please help, im sitting at the partitioner right now, nervously not wanting to go on without the answer haha

Mukaeutsu

---

### Post by Mukaeutsu on 2007-09-06
Also in addition, I read into info about the ext2fsd, and found that one drawback is that you cannot r/w LOGICAL drives from windows, what has been your experience with this, and is it okay to follow Luke771's advice on his common storage being logical?

Thanks everyone in advance.

---

### Post by Mukaeutsu on 2007-09-06
wow... as i am researching this, i am coming to more and more questions...
for the common storage, what do i place its mount point at and am i able to set installation of both Ubuntu and Windows programs and documents on this, with r/w access from both OS? (IE World of Warcraft- access from both OS needed)

Thanks again,
Mukaeutsu

---

### Post by merlinus on 2007-09-06
I have no problems writing to logical linux partitions from windows with the fs-driver.

You cannot run windows programs on linux filesystems, nor the reverse, unless in a vm or using wine.

For storage, you can use ext3 or ntfs.  I have no problems with the ntfs-3g driver for writing from linux.

-merlin

---


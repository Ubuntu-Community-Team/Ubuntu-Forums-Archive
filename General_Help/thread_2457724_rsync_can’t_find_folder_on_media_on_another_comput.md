---
title: "rsync can’t find folder on /media on another computer"
date: 2021-02-07
forum: General Help
---

### Post by anoldguy on 2021-02-07
I’m not sure if this is an Ubuntu or rsync issue.  
rsync 3.1.2, Ubuntu 20.04.2, Ubuntu 18.04.5.

The Ubuntu 20.04 is on the rsync destination computer.  The source computer is 18.04.  The source computer has a manually-mounted second SATA hard drive.  On the destination computer I run rsync to access the source computers second hard drive via SSH.  I get: 

receiving file list…
rsync: change_dir “/media/mememe/DiscDrive2” failed: No such file or directory (2)


The rsync source file path has:
ssh [email]mememe(at)bigbox.local[/email]:/media/mememe/DiscDrive2/MyStuff

I have tested an ssh session from the target to the source.  It connects and allows me to change directory to media, DiscDrive2, MyStuff, and files inside, so I feel that the SSH is working.  

Also, I use the same rsync target computer to copy files from a third Ubuntu computer that is running 20.04.  The difference is that the disc on the third computer is automatically mounted at boot time.  

The reason that I don’t automatically mount DiscDrive2 is that I also use SpiderOak on that drive, and I don’t want to upload the whole drive again from /mnt.  

Is there something different about the /media folder that is confusing rsync?  I think that the permissions all allow at least access.

---

### Post by TheFu on 2021-02-07
Is a real mount used or some sort of fake mount, like gio or gvfs?  Doe te mtab have the storage mount?
Also, what is the exact rsync command with full options? Hard to replicate without that.

---

### Post by anoldguy on 2021-02-08
Ah, thank you TheFu.  I hadn’t heard of fake mounts.

In Disks, in Mount Options, it shows User Session Defaults ON, and 
nosuid,nodev,nofail,x-gvfs-show

Disks shows the Mount Point as /mnt/[the UUID]
Identify As /dev/disk/by-uuid/[the UUID]


etc mtab has
/dev/sda /media/mememe/DiscDrive2 ext4 rw,nosuid,nodev,relatime 0 0
[What’s confusing to me is that if I go in through a terminal window on bigbox [Ubuntu 18.04], I can go to /media/mememe/DiscDrive2 and see my folders in there.]

Here is the rsync command that is run on the ‘storage’ computer [Ubuntu 20.04]:
rsync --verbose --time-limit=473 --delete-before -av --max-delete=73 --bwlimit=39876 --stats --progress -e ssh mememe(at)bigbox.local:/media/mememe/DiscDrive2/MyStuff /mnt/BigDisc3/DiscDrive2

Names have been changed to protect... me.


I did try to rsync with the ‘bigbox’ computer using DiscDrive2’s UUID, but same error message.

---

### Post by TheFu on 2021-02-08
That rsync command is wrong. Simplify and test.  There hasn't been any need to specify ssh for about 15 yrs.  Try:
```
$ rsync  -avz --delete-before --stats --progress  \
   mememe@bigbox.local:/media/mememe/DiscDrive2/MyStuff/   /mnt/BigDisc3/DiscDrive2/MyStuff
```
Trailing / is very important in the world of rsync.   Added the 'z' option, but only do that for networked transfers. It isn't useful for local transfers.

I've never used "Disks". Sorry. If it doesn't put something into the fstab, I wouldn't trust it.  
/dev/sda is an entire drive, not a partition. This is really bad and I'm surprised that it works at all.  File systems belong on partitions or LVs. 
Mounts should be using UUIDs or partition LABELs which don't change like devices files can.

I'm not a fan of using /media/ or /mnt/ for long term storage needs.  The *Linux File System Hierarchy Standards* are clear that is NOT the point for those locations. Both are for temporary needs, with /media/ for sometimes-connected, often USB, storage.  /mnt is for administration work - like a place to mount a file system only when testing or moving data from an old location before mounting it to the permanent location.  Whatever. Nobody listens/reads the documents anyway.

---

### Post by anoldguy on 2021-02-10
Thank you for the help TheFU.  Since I will need to re-upload 360 G bytes to SpiderOak [the source path is in /media], I will new-install Ubuntu 20.04 on the bigbox desktop.  Then I will grab a different disc and create a partition and have it mount at /dev.  Then I can copy my present DiscDrive2 contents onto the new partition.  Then back up to SpiderOak, and my LAN desktop via rsync.

Thank you for the rsync command.  I will still include the bwlimit [I had rsync bog my 1 GB LAN once with unlimited] and I will still include the max-delete [I made a typo once and rsync cleared a 2 T Byte disc drive]. 

Thanks for the reference to Linux File System Hierarchy Standards.  Some of my frustrations with Linux have been, difficulty finding a solution for your specific needs, that you find almost enough information to answer your question, and lack of enough examples.  

Thanks again TheFu for your help!

---

### Post by yancek on 2021-02-11
>  Then I will grab a different disc and create a partition and have it mount at /dev

I would definitely not do that.  Use the standard mount points you can create for your situation under the /mnt or /media direcories.

---

### Post by ActionParsnip on 2021-02-11
You can mount the remote server as SSHFS/SFTP then rsync between 2 folders as you expect, rsync can use SSHFS/SFTP itself though as shown in the rsync command earlier :)

---

### Post by TheFu on 2021-02-11
> **ActionParsnip said:**
> You can mount the remote server as SSHFS/SFTP then rsync between 2 folders as you expect, rsync can use SSHFS/SFTP itself though as shown in the rsync command earlier :)

Why mount via sshfs before rsync?  No needed 99% of the time, unless the remote system sucks and doesn't support ssh+rsync (which any Unix today should). No clue about spideroak. Sorry.
I suppose sshfs could be useful if running remote scripts is needed, but that's about the only time I use it.  sshfs is REALLY slow.  Sure, we mention it because it **is** another reason that ssh rocks, but the usefulness for that specific method is lacking.

But using sshfs wouldn't hurt as a test.

Every time I thought there was a big in ssh or rsync, I was wrong.  It was 100% my mistake.  Best to start with that assumption.

>  Then I will grab a different disc and create a partition and have it mount at /dev.
This better be a typo.  Doing that would be EXTREMELY bad.

I never use bwlimit unless I'm transferring files from remote systems and need to be kind for their uplink bandwidth.  Just never had rsync over ssh be able to impact even a GigE LAN - storage is almost certainly slower, unless everything is NVMe SSDs .... or you have crappy NICs that need CPU to work.

> lack of enough examples
lack of enough *experience* would be a better statement. The internet is full of examples - hundreds of thousands, if not millions.  Google-fu is an important skill, but sometimes we all have moments where we can't get the search terms right. ;(  Plus, our minds probably think in our "native" computer OS way.  Just like it takes a while to learn another language between we start dreaming in that language, Unix is the same if our brains are used to thinking in the way that some other OS taught.

---


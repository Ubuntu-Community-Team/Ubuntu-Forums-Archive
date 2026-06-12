---
title: "Partition woes"
date: 2007-06-14
forum: General Help
---

### Post by alatham on 2007-06-14
I've been using Ubuntu Studio for a few weeks now, but I was also multi-booting Windows XP and Mandriva 2007.  Last night I decided to remove the Mandriva install and use that space as a shared partition between XP and U Studio.

Before the changes:
```

Disc #1:
   Partition #1:
      NTFS (Windows)
   Partition #2:
      Mandriva /
   Partition #3:
      Mandriva /home
   Partition #4:
      Swap

Disc #2:
   Partition #1:
      U Studio /
   Partition #2:
      U Studio /home
   Partition #3:
      Swap

```

All the Linux partitions were EXT3.

So I used a Ubunutu Live disc (not the U Studio disc) to use GParted to edit the partitions to this:
```

Disc #1:
   Partition #1:
      NTFS (Windows)
   Partition #2:
      Fat32 (shared partition)

Disc #2:
   Partition #1:
      U Studio /
   Partition #2:
      U Studio /home
   Partition #3:
      Swap

```

Aside:  I would prefer to use a different file system for the shared space, but I think only FAT32 works under both Windows and Linux.  Does anyone have any suggestions?

I doubt it's important, but I had to unmount all the hard drive partitions in the Ubuntu Live OS (running from CD) in order to make changes to the disc.

So, I finished that and booted into XP to start moving files (without first checking to see if U Studio still worked).  Windows saw the space just fine, so I started moving all my media files to the FAT32 partition and went to bed.  When I woke up this morning, the first thing I saw on the monitor was a Linux prompt and error messages saying fdisk failed with error 8 (I think, this is from my shoddy memory).  I pressed alt+ctrl+backspace and it (surprisingly) took me to the U Studio log-in, but when I tried to log in I got the message that my /home folder couldn't be found and it immediately sent me back to the log-in.  U Studio will not start anymore (I even tried the failsafe mode and a different kernel, both of those failed too with the same problem).

I was told (by U Studio) that I need to manually reconfigure the file structure.  If that doesn't sound ominous, I don't know what does.

At that prompt I was able to navigate to the /home directory, but when I used ls, it showed nothing in that directory.

Boo.

So I booted into Windows, it worked (I don't believe in miracles, but this might count as one).  Once it started, I got a message saying that my computer had been updated and rebooted itself (which explains a few things).

So I guess I need to get U Studio to find my /home partition again.  It's somehow gotten lost.  I don't know if Windows finished moving files between partitions before it shut itself down, so there might have been some file corruption.  But at the same time, those two partitions are on the same physical disc, and U Studio is on the other disc by itself, so why would that affect how U Studio's file structure is set up?

I'm guessing that when I used the Ubunutu Live CD to change my partitions around, it somehow messed up how U Studio was configured.  I did notice that there was a small amount of unused space on the U Studio disc, but I think that's the space for EXT3's logging data (correct me if I'm wrong).

I'm at work now, but the next thing I'm going to do is use that Live CD to see if it can still see all my /home files.  After that I'll try using the U Studio disc to repair it's installation, unless someone suggests something better.

Thanks for any help or insight you can provide,
-Andy

---


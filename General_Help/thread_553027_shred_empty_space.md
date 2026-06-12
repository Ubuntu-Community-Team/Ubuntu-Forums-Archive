---
title: "shred empty space"
date: 2007-09-17
forum: General Help
---

### Post by gobbles414 on 2007-09-17
Hi all,

I am looking for a way to "shred" or "secure erase" unused disk space, like is possible in Mac OS X's *Disk Utility* and several 3rd party Windows programs. [The thread located here]("http://ubuntuforums.org/showthread.php?t=168210"), is not much help. Any Ideas? Thanks in advance for the help.

---

### Post by ddrichardson on 2007-09-18
From the command line, a seperate partition can be overwritten with zeros by```
 dd if=/dev/zero of=/dev/hda2
```
If you want something to secure unused space on one partition then try these:
[http://packages.ubuntu.com/feisty/utils/secure-delete](http://packages.ubuntu.com/feisty/utils/secure-delete)
[http://ubuntuforums.org/showthread.php?t=151699&highlight=wipe+shred+srm&page=2](http://ubuntuforums.org/showthread.php?t=151699&highlight=wipe+shred+srm&page=2)

---

### Post by mojoman on 2007-09-18
> **gobbles414 said:**
> Hi all,

I am looking for a way to "shred" or "secure erase" unused disk space, like is possible in Mac OS X's *Disk Utility* and several 3rd party Windows programs. [The thread located here]("http://ubuntuforums.org/showthread.php?t=168210"), is not much help. Any Ideas? Thanks in advance for the help.

You're dead on target, shred is the word. 

```
sudo shred FILENAME
```

Look at ```
man shred
``` for an more extensive explanation on the usage but it's a standard linux tool.

/mojoman

---

### Post by gobbles414 on 2007-09-18
Hi all,

Oops! I forgot to mention that I want to erase the free space on my boot partition. In Mac OS X, it is possible to erase free space on the boot partition will continuing to use the OS. That is my preference. But I am also willing to use the LiveCD if needed. Just to be clear, I do not want to erase ALL of the data on my disk. I just want to make sure that files which I have delete using the normal trash are entirely overwritten (I don't always have the time to shred my files as I am deleting them).

---

### Post by gobbles414 on 2007-09-18
ddrichardson,

I reread your post and decided to install secure-delete. It installed fine, but I cannot launch it in the terminal. How am I supposed to use secure-delete?

---

### Post by ddrichardson on 2007-09-18
No idea - is there an error message?

---

### Post by spd106 on 2007-09-19
Secure-delete is a package of four separate cli utilities, sswap, srm, sfill and smem. They each have man pages for correct syntax/options. 

As you have probably read, if you are using a journalled file system (eg ext3) it's not always possible to be sure the files have been shredded.

---

### Post by gobbles414 on 2007-09-24
Hi all,

I am using the ext3 format on my computer. So, I guess that means it is impossible for me to guarantee that my confidential data have been destroyed? Other suggestions on this issue are welcome.

---

### Post by ddrichardson on 2007-09-24
What do you mean by confidential data? If it's vital as it is on some of our systems then we use removeable drives that use encrypted filesystems. If you can't for whatever reason shred the files then powerful encryption would be the way ahead.

Incidentaly there is always a trade off between usability and security. Different standards also suggest different methods of erasing data to prevent reconstruction, our standard is random data writen to each sector sequentially up to five times. More often than not, old drives have this done then are physically destroyed (I do this and can assure you it's possibly the most fun you can have while wearing goggles).

---

### Post by HermanAB on 2007-09-24
Note that you *cannot* do secure erase on a modern journaled file system.  Trying to do that is just a waste of time.  If you think you can, then you are in for a surprise when push comes to shove.

Here are some details:
[http://www.cse-cst.gc.ca/publications/gov-pubs/itsg/itsg-e.html](http://www.cse-cst.gc.ca/publications/gov-pubs/itsg/itsg-e.html)
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

Therefore, the only way to securely erase data is to use an encrypted file system and 'forget' the key.  The military chuck used disk drives into a blast furnace at a steel mill.  For ordinary mortals, the precise application of a very big hammer is probably good enough.

Cheers,

Herman

---

### Post by ddrichardson on 2007-09-24
> **HermanAB said:**
> The military chuck used disk drives into a blast furnace at a steel mill.

For what it's worth, we do both. Even for systems designated only as "restricted". Most of the really sensitive stuff is on flash devices embedded within systems that use a master zeroise function to physically destroy them.

But the point is still valid - encryption is the way ahead, it depends on the sensitivity of data. Note I'm also talking about non-journalised systems.

---

### Post by ddrichardson on 2007-09-24
Anyway back to the original question - if using ext2 then [scrub]("http://www.llnl.gov/linux/scrub/") can do what you're looking for, it creates a file that uses all the free space (in this example junk), then erases it:
```
scrub -X /junk
rm /junk
```

---

### Post by JJNova on 2007-10-05
> **HermanAB said:**
> Note that you *cannot* do secure erase on a modern journaled file system.  Trying to do that is just a waste of time.  If you think you can, then you are in for a surprise when push comes to shove.

Your comment intrigued me, so I went ahead and did some researching, and to my dismay, you are absolutely correct. Not being able to completely erase information I think is a downfall or disadvantage of ext3 that more people should know about. I personally wish it was pointed out during the install process, as I have been using shred for a while now, just to learn that it's pretty pointless.

I don't delete the information to hide it from people in my family, I delete it in case the hard drive gets stolen. Permanent file removal is a very important thing for me. Thanks for your information.

---

### Post by JJNova on 2007-10-05
Ok, I just did a little more reading on shred and ext3. I read that the default for ext3 is not Journalled mode, but instead *data=ordered* mode.  So I'm wondering if this means my filesystem is *data=ordered*? If so, then shred is working perfectly.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6100d4d2-5da7-400d-980f-1c4a55b3b33b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=84018165-30c8-46a2-a0f1-00a10d8c7500 /home           ext3    defaults        0       2
# /dev/sda5
UUID=9ece3363-bae1-40dd-8533-27ada4c52489 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

As you can see, the options for both / and /home are *defaults* with / also having *errors=remount-ro*

---

### Post by atlfalcons866 on 2007-10-23
if ext3 is doing jorunal data ordered or journal data writeback its only jorunaling metadata which isnt the whole file so you can shred the space. Also ext3 zeros out the inode instead of marking it as deleted it does this to simplifie the jorunal some how

---


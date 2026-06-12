---
title: "I just wiped out my harddrive using dd....HELP!!"
date: 2014-02-11
forum: General Help
---

### Post by PDA1 on 2014-02-11
I just used DD to make an image to my big external hard drive (sdc) and wiped out over 350g of data.

The command I used was dd if=/dev/sdb of=/dev/sdc bs=4096 conv=notrunc,noerror

sdb was only 16g from a flash drive.

Please, please, please....someone...help me recover the data!!!!!

---

### Post by freebird54 on 2014-02-11
Afraid I can't be much direct help on this - but file recovery information is all over the web.  My experience with recovery is limited to SystemRescueCD - but a wealth of possibilities, tools and tutorials are out there.  I just didn't want to leave you unanswered...

Hope it helps - or that you find a 'reverse this ....up' command.

---

### Post by tgalati4 on 2014-02-11
You may get lucky.  The first 16 GB of the drive were probably Windows system files.  If they were linux files, you would lose 8 to 13 GB of data because a typical linux distro is around 5 GB of system files.

You may be motivated to read the following:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by PDA1 on 2014-02-11
What I was trying to do was make an image of my Crunchbang USB stick. The 500g drive *previously* to the disaster was only used for storage of files.

According to Gparted there are 450g of unallocated space on the drive. 

I just wasted over 2 hours running Testdisk with it not finding the missing partition or telling me much of anything.

The Testdisk forum has more unanswered questions than answered.

I'll try your suggestion for the DataRecovery...and think pure thoughts.

Thanks

---

### Post by sudodus on 2014-02-12
***dd*** is nicknamed 'disk destroyer' for a reason. I'm sure you will use a safer method next time you want to make an image of a drive, for example [Clonezilla]("http://clonezilla.org/"), or an installed system, for example the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971").

But like you have been told in the previous replies, I think there is hope to recover a lot of the files, if you are prepared to do a lot of hard work. The data that 'sit behind' the first 16 GB should still be there and available.

If you cannot get the file system back, there is always ***PhotoRec***. It can recover many kinds of files from the data found of the disk surface (without any partition table or file system). But the file names and directory structure are lost.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by PDA1 on 2014-02-12
Clonezilla? Have tried too many times and it's a mess to use. Redo is easier to understand.

Tried Testdisk. There's got to be a more understandable way to solve this.

---

### Post by sudodus on 2014-02-12
Using Clonezilla in beginner mode to make an image of a whole drive is not too difficult and definitely safer than dd (at least for me). You like ***Redo***. I have not tried it, but I have seen other people recommend it. One of the advantages with Linux is that there are many ways and tools to perform a task. It is often possible to find something for each person and task.

Sometimes Testdisk will find what you need, sometimes not. I'm not sure the problem is that you don't understand Testdisk. I think Testdisk can't find it. So you can try some of the other tools suggested or linked to ... and the last resort is PhotoRec, if you cannot find or re-create the partition table and file system.

---

### Post by PDA1 on 2014-02-13
Conclusion- failure

Tried- Seagate File Recovery (try before you buy) and it said the drive should be sent in to their lab$$$.

On the good side- there were backups of everything except some critical DVDs that I'll have to copy back to the new hard drive.

I once read, "Linux assumes you know what you're doing".

Obviously, I didn't.

---

### Post by sudodus on 2014-02-13
What a relief to read that you have backups of everything except some critical DVDs :-)

In this case restoring from the backup is way better than recovering files with PhotoRec.

---

### Post by monkeybrain20122 on 2014-02-13
Try fsarchiver. It is easy to use and safe. It is in the repo

[http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983](http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983) See post #8 for a brief instruction.

---

### Post by PDA1 on 2014-02-13
> **sudodus said:**
> What a relief to read that you have backups of everything except some critical DVDs :-)

In this case restoring from the backup is way better than recovering files with PhotoRec.

I'm leaving the messed up drive alone in the event someone comes up with an idea on how to recover the stuff. Sort of like the idea of those dopes that, after they die, are put into cryogenic capsules in the hope they can be revived in the future and that the cause of their death can be reversed.

Photorec? I used it for 8 hours yesterday. For whatever reason it didn't look at the entire drive. Just the existing allocated partition.

---

### Post by PDA1 on 2014-02-13
I'll take a look. 

Oh....the command that wrecked everything began with "dd". I noticed there's a program called DDrescue. What a sick joke that one was!

Thanks, folks, for trying to help.

---

### Post by PDA1 on 2014-02-13
> **monkeybrain20122 said:**
> Try fsarchiver. It is easy to use and safe. It is in the repo

[http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983](http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983) See post #8 for a brief instruction.


Say, I just looked at the posts about fsarchiver. That seems to be just what I need. In fact it mentioned that the entire archive is checksummed to protect against corruption.

Many thanks for your suggestion.

---


---
title: "Defragmenting after installing Wubi"
date: 2008-02-22
forum: General Help
---

### Post by GwilymHardy on 2008-02-22
I've had Ubuntu Feisty installed through Wubi for several months now. I didn't partition the drive to make a full, proper installation because I'd already had Windows installed for several years, and didn't understand how to partition safely. So I continue to use my Wubi installed Ubuntu.

Is it safe to defragment my PC whilst in WinXP, or will that screw up the file locations for my Ubuntu installation? I've searched for advice already given, and found nothing definite. 

Many thanks

---

### Post by kit.regan on 2008-02-22
It's perfectly safe to defrag your drive. Try JkDefrag, it is a much better tool than the default windows defragger.

---

### Post by cookieofdoom on 2008-02-23
Just confirmation. I did it yesterday with the default Windows defrag utility and I'm having no problems.:KS

---

### Post by 5nak3 on 2008-02-24
Can i ask when do you know it is time to defrag the drive once wubi is installed? I assume there may be slow downs and the likes?

And another thing, how does windows recognize and what does it do to the wubi files when it defrags? i would assume that it has them as unmoveable files

---

### Post by cookieofdoom on 2008-02-24
Defragmentation doesn't delete files (as far as I know), it moves them around on the physical hard drive to make the drive as efficient as possible. This article might help with that, as I'm not very good at explaining it...

[http://en.wikipedia.org/wiki/Defragmentation](http://en.wikipedia.org/wiki/Defragmentation)

As for when to do it, it's a good idea to do it on a Windows system once a week or so. If you're using most of your hard drive, doing it more often will help. If you're only using 10% or so of your hard drive, you can probably get away with doing it once a month. Defragmentation is not really necessary on ext3 Linux systems. I don't know about other file systems.

---

### Post by 5nak3 on 2008-02-24
Well since i am running wubi off of my NTFS drive, defrags would no doubt be necessary. But as long as i can do that without destroying the wubi install i dont mind doing so.

---

### Post by cookieofdoom on 2008-02-24
Oh, right. Somehow I managed to forget wubi was involved. Since the Wubi files are stored in NTFS you'll probably need to use Windows to defrag it. There aren't a lot of defrag utilities for Linux 'cause on most Linux file systems it isn't necessary.

You shouldn't have any problems with defragging from Windows.:cool:

---

### Post by DVG on 2008-06-15
I had a similar question about whether I could defrag my computer with Wubi and not mess Ubuntu or Windows up. I just got done running the Windows defrag on the whole system like normal and its fine. On the report it just says that it couldn't defrag /ubuntu/disks/root.disk, which makes sense, since that's the Ubuntu partition.

---

### Post by LibraDragon on 2009-04-10
I tried to use the latest JKDefrag in my Win Vista this morning and it went smoothly for all my partitions except the partition which stores the ubuntu file system. It hangs for at least 6 hours while trying to defrag this large file 'root.disk'. The screen reads
'M: Phase 2: Defragment     Moving  11080303 clusters from 436371 to 3499946
M:\Ubuntu\disks\root.disk
'Busy, please wait for redraw'

I would like to know if this is normal for such a large file or is it because JKDefrag really hangs? If so, how do I end the program?

---


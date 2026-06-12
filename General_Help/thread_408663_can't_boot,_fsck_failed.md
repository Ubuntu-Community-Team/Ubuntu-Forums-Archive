---
title: "can't boot, fsck failed"
date: 2007-04-13
forum: General Help
---

### Post by jchien on 2007-04-13
I recently installed Ubuntu via Wubi on my laptop. Unfortunately, my laptop is prone to crashes due to hardware, and after one crash I can no longer boot Ubuntu. I get the message that the fsck died with exit status 8.

The log says
```
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Invalid argument while trying to open /dev/loop6
/dev/loop6:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Fri Apr 13 15:19:24 2007
```

What can I do to fix this?

---

### Post by holz on 2007-04-14
Try to boot with a CD into rescue mode?

---

### Post by mac.ryan on 2007-04-14
My understanding of your problem is the following:[LIST]
[*]you installed ubuntu as an application into windows (i.e. you didn't partition your HD, but you mount image files as if they were partitions)
[*]the problem you get "fsck died with exit status 8" means that fsck had an "operational error". In my understanding of English (I am not a native speaker) this means that *fsck* simply didn't manage to run properly)
[*]you get the problem on */dev/loop6*, which means that the error is linked to one of the "virtual filesystems" (i.e. the images mounted as partitions)[/LIST]I have no direct experience whatsoever with wubi nor with loop devices, yet, the suggestion of "fixing" the "virtual partition" from an ubuntu liveCD, made by the poster above, makes sense to me.

In order to do that, you would probably need to follow the following steps:[LIST]
[*]launch the ubuntu liveCD
[*]mounting your windows partition in it (see [this]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop") for how-to)
[*]finding out where the virtual filesystem (normally a huge .img file) is.
[*]trying to mount that virtual filesystem into your liveCD (make your OS recognise the virtual filesystem with [losetup]("http://www.cl.cam.ac.uk/cgi-bin/manpage?8+losetup"))
[*]make a check with [fsck]("http://www.hmug.org/man/8/fsck.php") on it and see if you can fix the problems
[*]reboot normally and see if your wubi-installed ubuntu works again.[/LIST]Additional considerations:[LIST]
[*]I would strongly suggest you also try to find help on the wubi forums, as this problem seems to be very specific to the kind of installation wubi performs.
[*]Reading the wubi FAQ, the only downside of wubi is the slow access to HD. As you run it on a laptop (which HDs are notoriously slower than desktop), I am just wondering if it wouldn't be better for you to create a real partition, so to keep up a bit higher the overall speed.
[*]Given your prone-to-crash hardware, having a real EXT3 partiton (which has a journaling feature) would give you much more safety, as journaling is explicitly thought for minimising the effects of improper shutdown of a system.[/LIST]That is the further I could help you with my limited knowledge of GNU/Linux (but don't despair... somebody else with more experience might jump in!)

Best luck, and let us know if you overcome the problem and how! :)

---

### Post by jchien on 2007-04-17
Thanks for the tips. I ended up just reinstalling Ubuntu though. If I have another problem like this I'll take your advice.

---


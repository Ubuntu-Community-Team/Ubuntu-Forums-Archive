---
title: "Something happened to my wubi installation... Is all lost?"
date: 2012-10-27
forum: General Help
---

### Post by jayjay960 on 2012-10-27
Hey. So I had (have?) an installation of Ubuntu 10.10 through wubi that I use on my netbook, and I've been using it for well over a year.

Today while I was doing my usual thing I went to plug in the power to my netbook, and ubuntu froze. That in itself isn't unusual. I have a pretty crappy old netbook (I'm getting a new laptop in a couple of weeks) and this happens all the time. The only way to get around it is to do a hard restart via the power switch. 

When I went to restart, it started acting funny, and I kept getting various error messages about not being able to find devices and stuff while ubuntu was starting up. (Note: At this point ubuntu itself was definitely still working. These were al errors within ubuntu, not grub or anything). Again, this isn't unusual for my netbook, and I did another hard restart, which I've found is the only way to get past these problems.

This time when I restarted, when I tried to load Ubuntu a quick message flashed up about not being able to find a device, and I was sent to the grub prompt. I did some searching online, and apparently this is a problem which happens with a lot of wubi users. And the way to fix it is to edit the grub config files in a live CD. So I put in the CD I used to install Ubuntu. I mounted my Windows partition, /dev/sda1 (note that throughout all of this Windows was working fine). Then I had to mount Wubi's root.disk. Except it wasn't there. It ought to have been at /ubuntu/disks/root.disk (C:\ubuntu\disks\root.disk) but it's not. In fact, the disks folder itself isn't even there. This is what my ubuntu folder looks like:

```
+ install
    - .fuse_hidden0000000400000001

+ winboot
    - wubildr
    - wubildr.cfg
    - wubildr-bootstrap.cfg
    - wubildr.tar
    - wubildr.mbr

- Ubuntu.ico
- uninstall-wubi.exe
```

If something had happened to the disk, surely it would have just been deleted, and no other files or folders? I couldn't find root.disk anywhere else on the windows partition, but is there a chance it was installed somewhere else, or under a different name?

Are all the files on my ubuntu disk lost? Or is there any chance of recovering them? For what it's worth, my windows partition has  19GB free. I remember making the ubuntu disk small, but I think I would have at least given both the disk and my windows partition a bit of free space...

Edit: I downloaded one of those deleted file recovery programs on windows. I found a shitload of deleted files named "wubi.mo" that are all <20kb. Has that got anything to do with it?

---

### Post by bcbc on 2012-10-28
See this: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by jayjay960 on 2012-10-28
> **bcbc said:**
> See this: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

Thank you! I followed this and found my root.disk file in Windows. It must have been slightly corrupt or something because it kept giving me disk errors when I tried to move it back to C:\ubuntu\disks. But I ran it through a data recovery program, and it actually fixed it. I restarted, and GRUB and Ubuntu are actually working perfectly now. Phew, I though I'd lost everything there. Now excuse me while I go back up all my files... Twice.

---

### Post by bcbc on 2012-10-28
Good to hear! 

I have other tips on using Wubi on that blog. 
tl;dr, what I do is to synch data to Ubuntu One and store larger data (media content) on the /host or other partitions.

Also, I'm curious when you say that the file was still corrupted and you used some data recovery tool. Anything you can share might help others. 

Thanks

---


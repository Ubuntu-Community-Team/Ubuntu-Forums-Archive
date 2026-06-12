---
title: "Problems with ExFat file system."
date: 2015-02-09
forum: General Help
---

### Post by tachanchachi on 2015-02-09
Hey People!

I was doing some research some time ago because I needed a system file which was compatible with Windows, MacOS and Linux, and in addition capable of holding bigger than 4GB files. 
I found that exFat in principle could do it. So i formated my hard drives using this file system. 
However, I am now trying to do a backup of my old files and bringing a bit of order to my files and I encounter sometimes a strange problem. The external hard drive just would unmount alone when i try to move or copy files from one folder to a different one, 
giving me an error saying something like: 

 Transport endpoint is not connected

and i would need to unplug the disc, and plug it again. The files which are affected are usually always the same ones, and I would have no real access to them anymore in any way... Trying to read them or open them with a program would bring me the same error. 

Does somebody know how can I solve this? I would format my HD in a different file system, but right now I have no extra HD where I could copy between 1 and 2TB of data to be able to format the original drive. 

Thanks a lot in advance, and sorry if this is not the right forum to post, but I could not find a solution on the search bar... 

Cheers, 
Tachan

---

### Post by tachanchachi on 2015-02-20
Is there really no solution for my problem?

---

### Post by plucky on 2015-02-20
> **tachanchachi said:**
> Is there really no solution for my problem?

[This](http://ubuntuforums.org/showthread.php?t=2265638&p=13229887&viewfull=1#post13229887) might help.

Good Luck

---

### Post by raptir on 2015-02-20
Well, the error you're getting is a fuse error. You could try mounting it manually to see if that works any better...

```
sudo mount -t exfat /dev/sd* /media/[directory]
```

---

### Post by tachanchachi on 2015-04-17
Neither of both work. 

Any other ideas? 

I bought a new HD to copy the files on int, because I thought this one (great, now it is happening with two HD, both with ExFat) is broken. But I cant if I keep having the "Transport endpoint is not connected" error. I have of the order of 2 TB of information I can not loose... 
This is really annoying... :-@

---


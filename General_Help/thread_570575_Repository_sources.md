---
title: "Repository sources"
date: 2007-10-08
forum: General Help
---

### Post by LaRoza on 2007-10-08
I have use repository dvd's but I was wondering if I can just use the ISO of that DVD? My posts on the DVD player problem of my new laptop have been unanswered, even when I found the answer, but don't know how to proceed.

It will be easier to just use the ISO's anyway, can I add an ISO to Synaptic? If so, how?

Thanks.

---

### Post by zvacet on 2007-10-08
[http://ubuntuforums.org/showthread.php?t=352460]("http://ubuntuforums.org/showthread.php?t=352460")

---

### Post by FuturePilot on 2007-10-08
Never mind. I read to fast again:oops:

---

### Post by LaRoza on 2007-10-09
Sorry, my question was how to use the *iso*, not a dvd, because the dvd drive doesn't work, see: [http://ubuntuforums.org/showthread.php?t=570497](http://ubuntuforums.org/showthread.php?t=570497)

I have saved the ISO's, and wonder if I can use a virtual drive to mount a saved ISO image.

Also, how do I get Synaptic to stop telling me to insert a disk? The original install DVD is already added to the sources, and I wish to get rid of it, because it won't download from the internet.

---

### Post by FuturePilot on 2007-10-09
Open your sources.list and near the top there should be something referring to the CD. Just comment it out or delete it if you wish.
As for using the .iso. Goes something like this I think
```
sudo mount /my/image.iso /mountpoint -oloop
sudo apt-cdrom -d=/mountpoint add
```
I think the mount point has to be in fstab I think. I'm really not sure.

---

### Post by LaRoza on 2007-10-10
Thanks. I'll try it out.

I will probably use Gutsy in the future, and for now, I can get all the packages over a wired network at school. Just have to get build-essential, abiword, gcl, ruby, nasm and a few others.

---


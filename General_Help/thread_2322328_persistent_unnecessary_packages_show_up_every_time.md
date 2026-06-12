---
title: "persistent unnecessary packages show up every time I use apt-get"
date: 2016-04-27
forum: General Help
---

### Post by benji6 on 2016-04-27
I'm running lubuntu 15.10 on an old compaq laptop, and recently I've been seeing this message every time I run apt-get.

```
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-30 linux-headers-4.2.0-30-generic
  linux-image-4.2.0-30-generic linux-image-extra-4.2.0-30-generic
```

I've run autoremove, which claims to have removed them, showing this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.2.0-34 linux-headers-4.2.0-34-generic
  linux-image-4.2.0-34-generic linux-image-extra-4.2.0-34-generic
0 upgraded, 0 newly installed, 4 to remove and 16 not upgraded.
After this operation, 234 MB disk space will be freed.
```

I confirm I want to do this, the hard drive clicks around for a minute. It seems to have worked, but next time I install or update, or anything else from the terminal, it shows the same message. I've run autoremove several times to no avail. Finally, I ran to command to remove them manually, resulting in this message:

```
benji@Hal-nx5000-PL577UA-ABA:~$ sudo apt-get remove linux-headers-4.2.0-30 linux-headers-4.2.0-30-generic linux-image-4.2.0-30-generic linux-image-extra-4.2.0-30-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-headers-4.2.0-30' is not installed, so not removed
Package 'linux-headers-4.2.0-30-generic' is not installed, so not removed
Package 'linux-image-4.2.0-30-generic' is not installed, so not removed
Package 'linux-image-extra-4.2.0-30-generic' is not installed, so not removed
```

Are they there or not? What is autoremove doing? How can I finally make it go away?

---

### Post by deadflowr on 2016-04-27
Those are different packages.
One shows 4.2.0-30 and the other shows 4.2.0-34

Edit: Just to point that out

---

### Post by benji6 on 2016-04-27
ah, human error. Thanks for pointing that out.

Just ran the corrected command. packages are now actually gone.

Still curious why autoremove never worked. I'd like to leave this question open for a little while.

---

### Post by deadflowr on 2016-04-27
[s]What makes you think it didn't work?[/s]

Perhaps it has something to do with the 16 packages that can be upgraded.

---

### Post by benji6 on 2016-04-27
ah. I never paid attention to that part. However, it seems that wouldn't be the issue for two reasons. First, I don't see why the possibility for upgrades should prevent the removal of irrelevant packages. (I suppose it's possible that the program would wait until upgrades are complete to be sure they are truly irrelevant, but in that case I think it ought to generate an error message). Second, this has been a persistent issue for several weeks. I don't know that there were always upgrades available.

That said, I want to thank you again. Your observation was genuinely helpful. I hope I am not being belligerent in saying these things.

---


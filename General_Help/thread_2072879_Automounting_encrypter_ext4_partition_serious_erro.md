---
title: "Automounting encrypter ext4 partition: serious errors"
date: 2012-10-18
forum: General Help
---

### Post by astrobob.tk on 2012-10-18
I have this new issue with automounting but with an ext4 partition.

I'd like to automount the partition & so I added the following line to fstab:

```
UUID=<uuid> /media/data     ext4    defaults        0       2
``` 	 
I made the directory /media/data before that too.

At boot I'm getting the following error:

```
Serious errors were found while checking the disk drive /media/data
```

& promoted to Ignore, Skip, or manually mount.

What seems to be the problem?

Someone commented if it really is an ext4 or that it might be corrupted. Maybe since I didn't note that the partition was encrypted by disk utility. Does that make a difference??

thanks

---

### Post by astrobob.tk on 2012-10-21
bump

---

### Post by BenkartJKB on 2012-10-21
I had the boot prompt when I tried to automount an external usb drive. I changed the last number on a line to 0 and the prompt went away.  My guesses why this helped me would not help others reading this forum post.

---

### Post by astrobob.tk on 2012-10-22
> **BenkartJKB said:**
> I had the boot prompt when I tried to automount an external usb drive. I changed the last number on a line to 0 and the prompt went away.  My guesses why this helped me would not help others reading this forum post.

No that did not work!

---


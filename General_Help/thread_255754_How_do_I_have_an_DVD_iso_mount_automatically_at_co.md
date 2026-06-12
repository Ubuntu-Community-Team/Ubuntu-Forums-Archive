---
title: "How do I have an DVD iso mount automatically at computer bootup"
date: 2006-09-11
forum: General Help
---

### Post by fubadubrub on 2006-09-11
I have made an ISO image file of a DVD and would like to have it mounted automatically at every boot up of my computer.  Right now I have to login into my account and do this manually:

```
sudo mount /usr/local/DVD.iso /mnt/dvd/ -t udf -o loop
```

I need to automate this instead of doing it manually on every computer start up.  Also I use Edgy if that makes any difference.  Any help would be appreciated.

Thanks

---

### Post by Ocxic on 2006-09-12
there is a way to do what you ask (I think, this is mostly a guess but i know it's possible)
put this in your /etc/fstab edit to mach your setup: 
```

/media/file.iso /mount/point udf,iso9660 loop,defaults    0       0

```

---

### Post by fubadubrub on 2006-09-12
> **Ocxic said:**
> there is a way to do what you ask (I think, this is mostly a guess but i know it's possible)
put this in your /etc/fstab edit to match your setup: 
```

/media/file.iso /mount/point udf,iso9660 loop,defaults    0       0

```Did not work but thanks anyway.  I have decided to simply use a bash script to make the manual mounting command simpler.  I tried a whole bunch of fstab options but no go.  I Read the mount and fstab man pages and still no go.  Maybe I should have mentioned that the image file contains breaks like for example /usr/local/uh\ oh.iso

I thought for sure your idea would work.  Maybe breaks are at fault?

---


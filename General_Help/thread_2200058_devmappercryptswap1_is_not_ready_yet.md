---
title: "/dev/mapper/cryptswap1 is not ready yet"
date: 2014-01-17
forum: General Help
---

### Post by Azrael84 on 2014-01-17
I had this error on bootup, googled of course, and came across the various threads such as [this]("http://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or") , [this]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1153661") and [this one]("http://punygeek.blogspot.fr/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html").
I followed the instructions to the letter, and now when I run `free -m`, I can see my encrypted swap drive, and it is of the correct size. However, I still get the exact same error during boot:

```
/dev/mapper/cryptswap1 is not ready yet 
```

Why is that?

---

### Post by Azrael84 on 2014-01-17
[FONT=arial]Could it possibly be that the UUID of the swap partition seems to change with each boot (as far as I can tell from blkid), so the `/etc/initramfs-tools/conf.d/resume` set in the methods I linked to (presumably this attempts to mount that UUID, which we obtained at the time of issuing `mkswap`, in advance or some such?) is futile because the UUID of the swap changes? Just a theory....[/FONT]

---


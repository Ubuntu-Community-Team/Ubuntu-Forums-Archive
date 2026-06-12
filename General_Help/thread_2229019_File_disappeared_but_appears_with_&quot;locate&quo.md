---
title: "File disappeared but appears with &quot;locate&quot;?"
date: 2014-06-10
forum: General Help
---

### Post by linux_dream on 2014-06-10
Hi people,
I just noticed that one of my files (sfbooker.bin) disappeared as if I had removed it. When I type locate "sfbooker" I see ```
/usr/local/share/scid/books/sfbooker.bin
``` which is where the file is supposed to be.
However when I go there either with PCmanFM or with the terminal and type "ls", I see absolutely no file in /usr/local/share/scid/books.

I have typed "sudo updatedb" and retried the "locate sfbooker" and it still returns ```
/usr/local/share/scid/books/sfbooker.bin

```.

So I don't understand what's going on. Have I lost my file? If so, how is that possible? The file was set in such a way that only root could modify/delete it and I never deleted it. And if it's deleted, why does it appear with the locate command?

I tried the live CD (via an usb stick) of Lubuntu 14.04 and mounted my everyday's Lubuntu partition. The file sfbooker.bin is still invisible... I also ran fsck (via the live cd) this morning and no error was reported.

---

### Post by bab1 on 2014-06-11
> **linux_dream said:**
> Hi people,
I just noticed that one of my files (sfbooker.bin) disappeared as if I had removed it. When I type locate "sfbooker" I see ```
/usr/local/share/scid/books/sfbooker.bin
``` which is where the file is supposed to be.
However when I go there either with PCmanFM or with the terminal and type "ls", I see absolutely no file in /usr/local/share/scid/books.

I have typed "sudo updatedb" and retried the "locate sfbooker" and it still returns ```
/usr/local/share/scid/books/sfbooker.bin

```.

So I don't understand what's going on. Have I lost my file? If so, how is that possible? The file was set in such a way that only root could modify/delete it and I never deleted it. And if it's deleted, why does it appear with the locate command?

I tried the live CD (via an usb stick) of Lubuntu 14.04 and mounted my everyday's Lubuntu partition. The file sfbooker.bin is still invisible... I also ran fsck (via the live cd) this morning and no error was reported.

Post the output of ```
stat /usr/local/share/scid/books/sfbooker.bin
```

---

### Post by linux_dream on 2014-06-11
> **bab1 said:**
> Post the output of ```
stat /usr/local/share/scid/books/sfbooker.bin
```
```
stat: cannot stat ‘/usr/local/share/scid/books/sfbooker.bin’: No such file or directory
```

---

### Post by philinux on 2014-06-11
Linux_dream,

You may need to run sudo updatedb then rerun locate. Locate could be looking at the old database.

---

### Post by bab1 on 2014-06-11
> **bab1 said:**
> Post the output of ```
stat /usr/local/share/scid/books/sfbooker.bin
```
This tells me that the file no longer exists.

---

### Post by linux_dream on 2014-06-11
> **philinux said:**
> Linux_dream,

You may need to run sudo updatedb then rerun locate. Locate could be looking at the old database.Well as I wrote in the first post, I've already done this (now maybe 10 times since then, and the file still appears with the locate command.)

> **bab1 said:**
> This tells me that the file no longer exists.
Okay. I would like to understand linux though. Why does "locate sfbooker" still points at an empty folder, even after I typed "sudo updatedb"?
And what are the possible reasons a file could disappear on its own like that one?
That is very scary... I mean, I feel like any file could simply disappear, even if it's in read-only and can only be modified with "sudo"...

---

### Post by steeldriver on 2014-06-11
Is /usr/local (or any of the directories below it - /usr/local/share, /usr/local/share/scid, /usr/local/share/scid/books) on a separate partition/filesystem?

---

### Post by linux_dream on 2014-06-11
> **steeldriver said:**
> Is /usr/local (or any of the directories below it - /usr/local/share, /usr/local/share/scid, /usr/local/share/scid/books) on a separate partition/filesystem?
No, same partition. I only have 2 Windows partitions, 1 swap and 1 Lubuntu (ext4 file system).

---

### Post by linux_dream on 2014-06-12
Mystery solved:
The file is indeed deleted (probably due to that I shut down my computer the hard way due to a a freeze).
Why did locate still point at an empty folder despite having typed "sudo updatedb"? Well because apparently sudo updatedb only adds locations of new files but doesn't remove old ones.
So I had to delete a file ```
dd if=/dev/zero of=/var/lib/mlocate/mlocate.db
``` or ```
sudo bash -c "cat $>  /var/lib/mlocate/mlocate.db"
```. And then "sudo updatedb" again.
Then "locate sfbooker" does not return anything as expected.
Problem solved.

---


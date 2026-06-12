---
title: "crypt header backup file"
date: 2023-11-28
forum: General Help
---

### Post by sniper8752 on 2023-11-28
I was going through an old hard drive of mine, and found the following file: toshibahdcryptheaderbackup.img.  
Does this have to do with LUKS encryption?  Does it allow me to perform some kind of recovery?

---

### Post by TheFu on 2023-11-28
What does 
```
$ file toshibahdcryptheaderbackup.img
```
say about the file?

Looks like you named the file to me.

---

### Post by MAFoElffen on 2023-11-29
Which... Eevn if it is a LUKS header backup... You might need the details of how it was created to restore it over a corrupted header. As long as there was no offset... That's where that get's tricky.

---

### Post by MAFoElffen on 2023-11-29
Which... Even if it is a LUKS header backup... You might need the details of how it was created to restore it over a corrupted header. 

That start out the same, at 0 offset:
```

0x4c55 0x4b53 0xbabe

```
But the end bytes of the headers are different for each type at different offsets...

More details: [https://security.stackexchange.com/questions/227359/how-to-determine-start-and-end-bytes-of-luks-header](https://security.stackexchange.com/questions/227359/how-to-determine-start-and-end-bytes-of-luks-header)

---


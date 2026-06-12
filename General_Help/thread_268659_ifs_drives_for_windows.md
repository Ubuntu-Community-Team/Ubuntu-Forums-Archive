---
title: "ifs drives for windows"
date: 2006-09-30
forum: General Help
---

### Post by Polygon on 2006-09-30
so... i installed ifs drives on windows (allows me to read/write from ext3 and ext2 partitons in windows) and i currently have a seprate ext3 partiton which i keep all my windows documents, music, pictures all that

it seems to work very well, except that yesterdway when i booted up it gave me an error saying that "win data" (my windows ext3 partiton) has encountered errors, and something along the lines of "volume contains big files by there is no "FILE_BIG" flag on the superblock" or something. and it also told me to do a fsck or something on the partiton

I thought that using ifs drives wouldent screw up my partitions.... is it safe to keep using this? and if so, will a fsck fix whatever problems without damaging my files? and how do i prevent this problem from happening again?

---

### Post by Polygon on 2006-09-30
bump

---

### Post by Polygon on 2006-10-01
come on i want this fixed =/

---

### Post by Polygon on 2006-10-01
ok since no one answered me i decided to take a crack at this myself, and i fixed it, and here is how:

i googled some things and came across this:

[http://service.dell.com/dell/series/1,,33734+47+26179+25950,00.html](http://service.dell.com/dell/series/1,,33734+47+26179+25950,00.html)

basically what i did: (after i backed everything up, cause someone told me that there is a slim possilibity of data loss, or some stuff being moved to lost+found or something)

```
cat /etc/fstab
```

found the drive that was generating errors, for me it was /dev/hdb3

```
sudo umount /dev/hdb3
```

unmounted the drive so fsck could check it

```
sudo fsck /dev/hdb3
```

then it did the check, and i didnt get any output besides what it was checking, and then it exited out on its own. Upon restart, i dont get any "filesystem contains errors" anymore and i can still read /write to it

---


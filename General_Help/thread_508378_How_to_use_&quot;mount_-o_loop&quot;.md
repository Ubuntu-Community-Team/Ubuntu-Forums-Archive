---
title: "How to use &quot;mount -o loop&quot;"
date: 2007-07-24
forum: General Help
---

### Post by PaulFXH on 2007-07-24
I'm trying to include some additional modules in a initrd.img file (not from Ubuntu, but I'm carrying out the changes in Ubuntu).
The traditional method to do this (because the initrd.img is a compressed file) is

```
mv initrd.img initrd.img.gz
gunzip initrd.img.gz
mkdir initrd
mount -o loop initrd.img initrd
```
The first line just renames the compressed initrd.img to something that the gunzip command will recognise. Then it is decompressed in the next line to provide another file named initrd.img (but this time it's de-compressed).
To facilitate access to the files/folders in the "new" initrd.img file, it needs to be mounted in a newly created folder (initrd).
Because its not a block device the "-o loop" mount option must be used.

My problem is that I can't get the "mount -o loop" command to work.
If I try it as shown above I get this error:
```
 mount: you must specify the filesystem type 
```
If I change the mount command to 
```
  sudo mount -t ext2 -o loop initrd.img initrd
```
I get this error
```
  mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Can anybody see what might be wrong here?

Thanks 
Paul

---

### Post by kuja on 2007-07-24
Are you sure you're specifying the correct filesystem type?

---

### Post by PaulFXH on 2007-07-24
Hmmm, yes that's a good point. My choice of "ext2" was simply based on "hearsay".
However, when I run a "file" command on the unzipped file I get this:
```
paul@paul:~/Desktop$ file initrd.img
initrd.img: ASCII cpio archive (SVR4 with no CRC)
```
which has no mention of "ext2"
Nevertheless, my primary concern is still why I get this error message regarding the need to specify the FS when the "mount -o loop" command seems to be very widely used by others to gain access to initrd.img files without any refernec to the FS.

---


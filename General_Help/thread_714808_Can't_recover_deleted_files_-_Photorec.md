---
title: "Can't recover deleted files - Photorec"
date: 2008-03-04
forum: General Help
---

### Post by shelbydz on 2008-03-04
Hey guys, 

I'm trying to use Photorec to recover some lost data. It was just deleted off the disk, it wasn't formatted or repartitioned or anything like that. 

When I run photorec and let it do it's thing, it's coming back w/ thousands of txt files that look like code and hundreds of partial MP3s that don't play. I have a bad feeling that this is my lost data, but in chunks that i won't be able to repair. 

The stuff that does come back whole is ONLY the browser cache, scores of tiny GIFs and JPEGs from websites that I've visited recently, not even cache that i've possibly cleared. 

Am I missing something while using photorec, or am I just hosed? 

thx

---

### Post by az on 2008-03-04
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

Use dls from the sleuthkit to put al lthe unallocated blocks on your partition to a file.  Then data-carve the files you want out of that file.  That will rescue only the deleted files from your system.  Use foremost or photorec for data carving.

You can then sort your recovered images and mp3s using find and jhead.

---

### Post by shelbydz on 2008-03-04
when i run:
```
/media$ sudo dls -f ext /dev/hda5 /dev/sda1
```
I get
```
Read offset too large for image file (split_read_random - 1024 - No such file or directory) (ext2fs_open: superblock)
```

The FS on /dev/hda5 is EXT3, so it does that wierd split thing. I'm having trouble getting dls to work properly. Any ideas? /dev/hda5 is ~100gb, and /dev/sda1 is ~500gb, so there shouldn't be a space issue.

thx.

---


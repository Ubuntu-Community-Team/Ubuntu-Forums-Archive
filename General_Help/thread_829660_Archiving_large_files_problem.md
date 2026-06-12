---
title: "Archiving large files problem"
date: 2008-06-15
forum: General Help
---

### Post by nirkir on 2008-06-15
I'm trying to tar+gzip some large files into a single archive. The problem it that when the resulting file size is larger than 4GB I'm getting a gzip error (File too large).

Is there a way to workaround that? Is there a different method to compress large files?

---

### Post by cariboo on 2008-06-15
There is bzip2 check out the man page. In a terminal type:

```
man bzip2
```

Jim

---

### Post by niteshifter on 2008-06-15
Hi,

You wouldn't be attempting to do this (make the archive) on a VFAT (or FAT32) file system per chance? If so, that's your problem: the 4GB limit of VFAT/FAT32.

bzip2 will give better compression, but with a penalty: time. It takes longer. Much longer. Make that much, much, much longer.

The thing is, with tar or gzip or tar+gzip for really big archives, it can be slow going. There's a lot of file I/O going on. It can be helpful to:

A) Make the really big file into a set of smaller pieces.
B) Make the output of the compression into smaller pieces.

Although your stated problem is with file sizes, one of those two above may prove useful.

The split command is what you need (this is A, above):
```
split --bytes=2000m --numeric-suffixes reallybigfile reallybigfile.part.
```
Will take the file "reallybigfile" and split it into chunks:
reallybigfile.part.00
reallybigfile.part.01
.
.
reallybigfile.part.NN

where each chunk is 2GB in size. You could then tar+gzip the set. You put the pieces back together after un-tarring with:
```
cat reallybigfile.part.* > reallybigfile
```

You can combine gzip and split (this is B, above):
```
gzip --stdout bigfile | split --bytes=2000m --numeric-suffixes - bigfile.gz.part.
```
Note the dash after --numeric-suffixes, it's important. The above produces:
bigfile.gz.part.00
bigfile.gz.part.01
.
.
bigfile.gz.part.NN


You can then tar the collection of files (sans the -j or -z options as they are already compressed).

You put the parts back together in a single file with:
```
cat bigfile.gz.part.* > bigfile.gz
```

More details and the short, one character option forms in the man pages:
```
man split
man gzip
```

---

### Post by nirkir on 2008-06-17
Hi all,

Thanks for the quick responses. Indeed I'm using FAT-based disk (external USB HD which comes formatted as FAT out of the box). 

I can simply change the filesystem on this disk - this should do the trick. However I'm bothered by the performance issues that niteshifter raised.

The problem is that I'm using this for backup. Therefore I'm trying to avoid splitting and catting the file (wouldn't this process take some time as well?)

I think I'd either take my chance with changing the filesystem and see whether performance is tolerable. If not - I'll see if the splitting works for me.

Thanks for the advice.

---

### Post by gollum2000 on 2008-06-17
Thanks niteshifter, useful tips. ;)

---

### Post by bingoUV on 2008-06-17
There are no performance problems. Just change your filesystem to ext3/NTFS or other. There is indeed a lot of I/O going on, but it would not reduce just because you split the file into many parts. Add the overhead of splitting the file and now your compression is taking longer than when not split

A variation of the method niteshifter pointed out can be made to improve performance when using multi-core CPU. After splitting the file, it is compressed in parallel. Even there, since gzip in default settings is quite fast the bottleneck is mostly disk I/O. More performance gains can be had when you use bzip2, or gzip with -9 option.

---


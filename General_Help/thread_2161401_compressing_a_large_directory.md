---
title: "compressing a large directory"
date: 2013-07-10
forum: General Help
---

### Post by akhil2091 on 2013-07-10
So here's the problem: everytime I try to compress a folder (right-click->compress, .7z) thats larger than say 3GB (approx), my laptop shuts down. 
Doesn't crash, hang, or give any error. It shuts down as normally as if I'd done Power button->shut down!

At first I thought this was a problem with the Ubuntu archive manager (File Roller). I have Windows 7 installed (on VMWare) so I tried to do the same thing with WinZip. I got the same result (Ubuntu shut down, not the VMWare Player).

When i installed Ubuntu, I seperated the /tmp and /var onto different partitions. They're on 3GB and 5GB partitions respectively. Is it because there isn't enough space on them that I cannot get large folders into archives?

I need to compress and lock a folder of almost 50GB before I transfer it to my external hard drive. How can I do this? I've heard of large compression tools like lrzip but they're not what I'm looking for. I merely need to lock this folder into an archive with a password.

Any help is much appreciated.

---

### Post by TenPlus1 on 2013-07-10
It sounds as if your laptop is overheating due to processor usage in compressing that big a directory, maybe you could try encrypting your home directory in Ubuntu so that only you can gain access...

---

### Post by sudodus on 2013-07-10
It could be the limit of /tmp, that is causing your problem. Nowadays it might be a good idea to have only a root partition or a root partition and a home partition, plus a data partition (maybe like you plan to use the external hard drive). This way it will be easier to use the free space wherever it is needed.

Anyway, there are tools, that should work without the restriction you are experiencing now. For example, you can make a compressed copy, a tarball, on your external HDD with tar (+ gzip). Or you can make an image with Clonezilla. But remember that most multimedia files are already well compressed, so there is no reason to compress them, they can be copied as they are, which is more convenient. So you need compress only the other files, which I hope is much smaller than 50 GB.

If you copy/write the compressed archive/image directly to the external drive (instead of trying to compress while still on the internal drive), it should work with either of those methods (tar, clonezilla).

*Edit*: Actually, I think ***tar*** would be a good choice for you.

---

### Post by akhil2091 on 2013-07-10
> **sudodus said:**
> 
Anyway, there are tools, that should work without the restriction you are experiencing now. For example, you can make a compressed copy, a tarball, on your external HDD with tar (+ gzip). Or you can make an image with Clonezilla. But remember that most multimedia files are already well compressed, so there is no reason to compress them, they can be copied as they are, which is more convenient. So you need compress only the other files, which I hope is much smaller than 50 GB.

If you copy/write the compressed archive/image directly to the external drive (instead of trying to compress while still on the internal drive), it should work with either of those methods (tar, clonezilla).

*Edit*: Actually, I think ***tar*** would be a good choice for you.

The reason for "compressing" isn't to reduce the size actually. Most of the files in that folder are audio/video so I know they can't be compressed further. The reason is that I want to secure that folder with a password, and the simplest way to do this is to put it in a .7z archive. .tar doesn't allow password protection (at least not when you do right-click->compress). I tried tools like cryptkeeper and truecrypt but again they're not exactly what I want. 

Even if I directly compress the folder onto my external HD won't the /tmp still be used? I mean, I tried doing this on a virtual OS and it still used my /tmp although it was stored in /home so I don't quite understand how that will work.

---

### Post by sudodus on 2013-07-11
> **akhil2091 said:**
> The reason for "compressing" isn't to reduce the size actually. Most of the files in that folder are audio/video so I know they can't be compressed further. The reason is that I want to secure that folder with a password, and the simplest way to do this is to put it in a .7z archive. .tar doesn't allow password protection (at least not when you do right-click->compress). I tried tools like cryptkeeper and truecrypt but again they're not exactly what I want. 
I see.
> 
Even if I directly compress the folder onto my external HD won't the /tmp still be used? I mean, I tried doing this on a virtual OS and it still used my /tmp although it was stored in /home so I don't quite understand how that will work.
My experience is that tar is [compressing and] writing as the work continues, so it will not need a huge workspace in /tmp.

Maybe a solution for you is to create a new user with encrypted home, and from that user 'import' the huge directory (copy it from the other user to it's own home directory). Then it will be automatically encrypted (but will appear in clear text while logged in as this new user). Make a good password at once, such that it is easy for you to remember and hard for other people or machines for guess. This password should not be changed.

Depending on the flavour you are using, you may or may not have ***users-admin***. It can be installed with

```
sudo apt-get install users-admin
```

and there is an option to select encrypted home, when you create a new user.

---


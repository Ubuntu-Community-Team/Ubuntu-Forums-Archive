---
title: "Gzipped ISO"
date: 2008-01-27
forum: General Help
---

### Post by elicoten on 2008-01-27
Is it possible to mount a gzipped ISO image? Or is it possible to, for example, play it in VLC (its a DVD image) without first completely uncompressing it?

Also, Is it possible to un-Zip it when the amount of free space on the drive is less than the total size of the uncompressed image?

Thanks for any advice

---

### Post by jpeddicord on 2008-01-27
As far as I know, no you can't. To read data from the archive, it has to be extracted somehow. This theoretically could be done in memory, but you will probably need a lot of it. I'm not sure of any tools that can do that either; usually it is application-specific (ie, the media player needs to support it).

Unless the player you are using supports gzipped videos, I don't think it will happen.

---

### Post by ryanVickers on 2008-01-27
As for having enough space to hold an extracted version, yes, you need enough free disk space to hold the file if you plan to extract it.

---

### Post by elicoten on 2008-01-28
Does anyone know of a media player that can play gzipped iso images?

Essentially you are basically saying that this ISO file is useless on this computer without adding extra storage space to decompress it? (The compressed ISO is larger than the free space available).

---

### Post by ryanVickers on 2008-01-28
yes, basically, if you cannot hold an extracted version, the file is useless.  To avoid raising the argument of "why do we bother compressing things anyways then?", I will answer by saying that usually an archive is many smaller individual files that could be temporarily extracted for use.

---

### Post by elicoten on 2008-01-29
Yeah I understand the argument, I was just wondering if there was any way to take advantage of it even further. In Windows you can still open compressed files (if you use the built-in NTFS file-system compression) without having any extra software or decompressing the whole thing. But I understand that's not the same as a gzip archive - even on Windows you would have to totally extract a gzip archive to use it.

Is there any similar file system compression in ext3?

---

### Post by ryanVickers on 2008-01-29
> **elicoten said:**
> Yeah I understand the argument, I was just wondering if there was any way to take advantage of it even further. In Windows you can still open compressed files (if you use the built-in NTFS file-system compression) without having any extra software or decompressing the whole thing. But I understand that's not the same as a gzip archive - even on Windows you would have to totally extract a gzip archive to use it.

Is there any similar file system compression in ext3?

No, there isn't.  The reason this works is because as a compressed file, it's just that - a compressed file, on a normal filesystem.  In Windows, the raw file is on the disk, not in an archive, and it is simply read from disk in the compressed form.  In theory, there is no reason why this could not be done on Linux, and why a file could not be read like this from within the archive, but as life sands today, no such feature exists :(

---


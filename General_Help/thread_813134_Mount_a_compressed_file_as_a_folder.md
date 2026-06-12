---
title: "Mount a compressed file as a folder?"
date: 2008-05-30
forum: General Help
---

### Post by Endolith on 2008-05-30
Is it possible to mount a compressed file (like .tar.gz or .bz2) without decompressing it?

For instance, I can mount an ISO file (which holds the filesystem for a CD-ROM) without actually burning it to a CD:

```
sudo mount -o loop ~/isofile.iso /media/cdrom0
```

I want applications to be able to access the contents of the compressed file as if they were inside a normal folder, without expanding the file to my drive.  (The files I want to read have a very large compression ratio, and I don't care about access speed.)

Yes, I've already googled this, and I can't find any actual commands that will do it.  There are some programs that say they do it, but they seem to be abandonware.  There are commands like zless, bzdiff, and bzgrep that operate on the contents of compressed files, but I want to do more general things with the contents.

---

### Post by bingoUV on 2008-05-30
Have you seen this? [http://www.linux.com/feature/132196](http://www.linux.com/feature/132196) . Seems recent. Gutsy package might even work for hardy.

---

### Post by Endolith on 2008-05-30
> **bingoUV said:**
> Have you seen this? [http://www.linux.com/feature/132196](http://www.linux.com/feature/132196) . Seems recent.

That looks promising, thanks.

> Gutsy package might even work for hardy.

The Gutsy packages are for libarchive, which looks to be in the repositories already.  archivemount is not, though.

Does anyone know of a method that's built into Ubuntu?

---

### Post by Endolith on 2008-05-31
Uh... I compiled something from source.  For the first time in my life!  And it works!  First you have to ```
apt-get install libarchive-dev libfuse-dev
```Then ```
./configure
make
```Then you can type ```
./archivemount filename.tar /tmp/location
```and it will behave as if the tar file is a directory!  Got it to work with a .tar and a .tar.bz2, but it doesn't seem to work for a single file inside a .bz2

I can put a single file inside a .tar.bz2, and that works, but the same file inside a .bz2 creates an empty directory, even though it otherwise behaves as though it's mounted something.

---

### Post by Endolith on 2009-09-22
Now we have the "Archive Mounter" tool on right-click. I wonder how it works. Does it expand the contents to /tmp or something?

The .desktop file has this:

```
Exec=/usr/lib/gvfs/gvfsd-archive file=%u
```

I can't find any documentation for how gvfsd-archive works.  I guess I'll find out when I try mounting a several-GB .bz2 later.

---

### Post by Endolith on 2009-09-23
Archive Mounter does not work on single-file archives like .bz2.  Only .tar.bz2.  :(   

Is there anything like archivemount built into Ubuntu?

Actually I guess they're pretty similar.

"**archivemount** is a [FUSE]("http://en.wikipedia.org/wiki/Filesystem_in_Userspace") based file system for Unix variants" "archivemount depends on [libarchive]("http://people.freebsd.org/%7Ekientzle/libarchive/") for the heavy lifting."

Supported backends for GVFS "include ... archive mounting support (through libarchive). For components that don't currently support GVFS URIs, the GVFS-Fuse module is used, which gives absolute paths to applications, mounted under a folder in the user's home directory."

---

### Post by Endolith on 2009-09-23
I guess neither tool can mount a single-file archive.  Is there a way to decompress and pipe the output to recompress it without expanding the entire thing to memory?  

[http://ubuntuforums.org/showthread.php?p=7997235](http://ubuntuforums.org/showthread.php?p=7997235)

---


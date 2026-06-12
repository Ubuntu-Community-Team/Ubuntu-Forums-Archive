---
title: "Archiving broken"
date: 2024-09-20
forum: General Help
---

### Post by helpwiththerapture on 2024-09-20
Archiving seems to be completely broken when it comes to symbolic links, which as a developer I depend on a lot.

I have a directory containing links, a mixture of relative, absolute, and links to folders:

DeadLink_abs -> /a/b/c/DeadLink_abs
DeadLink_rel -> ../../DeadLink_rel
file_abs -> /home/me/file1
file_rel -> ../../file1
Pictures -> ../../Pictures/

I want to archive this, e.g. to a 7z. I just want to store the symlinks as symlinks, whether dead, alive, relative or absolute.
 Used to be fine, but now it breaks in numerous different ways depending  exactly what it in the directory, which compression type, and how I run  it (command line or GUI).

Right clicking and selecting Compress... takes a while then just exits, no file.
7z command line does something similar, but fails on the dead links.
Both tools seem to be trying to add all the Pictures directory, instead of just **archiving the symlink**s, which is how it always used to work.
If I select Compress...and choose .tar.gz I get the links, but the linked directory is deferenced and includes the files.

The only tool that seems to work is tar.gz .... for now.
What's going on please?

---

### Post by TheFu on 2024-09-20
You could create a tar file, then use 7z to compress it, but that would be non-standard.  Tar is designed to work on Unix-like OSes, so it has supported symlinks for decades.  ZIP was created for MS-DOS which doesn't support symlinks - heck, NTFS didn't support symlinks correctly until after Win7.

Use the right tool, for the right job.  That's about all I can say on this.

You can use a number of compression tools (gzip, bzip2, xz, compress, others ... ) with tar files, if you like.  GnuTar has support built-in for compressing and decompressing ... let me check the manpage, 
```
       -j, --bzip2
              Filter the archive through bzip2(1).

       -J, --xz
              Filter the archive through xz(1).

       --lzip Filter the archive through lzip(1).

       --lzma Filter the archive through lzma(1).

       --lzop Filter the archive through lzop(1).

       --no-auto-compress
              Do not use archive suffix to determine the compression program.

       -z, --gzip, --gunzip, --ungzip
              Filter the archive through gzip(1).

       -Z, --compress, --uncompress
              Filter the archive through compress(1).

```
Or any other, compression tool using the 
```
       -I, --use-compress-program=COMMAND
              Filter data through COMMAND.  It must accept the -d option, for decompression.   The  argument  can
              contain command line options.
```
Lots of options.  You may notice that ZIP tools aren't built-in. I'd guess that's because there are too many variants which make compatibility difficult.

BTW, if root/sudo isn't used with tar, no absolute paths will be stored.  The leading / will be removed, thus retaining the directory structure, but it won't be restored from / down, unless sudo/root is used for the **tar x.... ** de-archiving.

---

### Post by ActionParsnip on 2024-09-21
Could make a tar then cosmpress it with 7zip.

---

### Post by helpwiththerapture on 2024-09-22
The point is not how to use tar in creative ways, the point is that *all* archiving tools are broken in a recent update of Ubuntu 24.04, except tar (for now). Is this problem acknowledged? It is going to be fixed? 
Why are symlinks considered not all that important anymore?

---

### Post by TheFu on 2024-09-22
> **helpwiththerapture said:**
> The point is not how to use tar in creative ways, the point is that *all* archiving tools are broken in a recent update of Ubuntu 24.04, except tar (for now). Is this problem acknowledged? It is going to be fixed? 
Why are symlinks considered not all that important anymore?

Symlinks are absolutely critical!  We use them all the time, but we typically use tar with archives and different compression tools than 7zip.  You are right - it should work.  

a) did those tools all work the way you think they should in prior releases on any Linux?  Are you using the **-l** option?
b) Nobody here works for Canonical.  We are volunteers trying to get you passed the issue, often with workarounds, if not solutions.
c) Canonical didn't create any of those compression tools.  If you have a complaint, best to go to the specific project team and open a bug with them.  You can open a bug with Canonical, if you like, but the project team will need to be paying attention to it and address it.

It is good to get other opinions before opening a bug. The best situation you can hope for it that a future release of 7zip corrects the problem AND they add an test case to their automatic testing solution so it isn't missed in the future.  Then hope they provide a PPA so you can get the newer version into Ubuntu.

We provided a workaround in our posts. Nothing more.  Use tar and one of the built-in compressors that it supports. I use tar.gz or tar.bz2 files because they are built into the tar program.

If I need ZIP compatibility with other OSes, I tend to use PeaZIP because it is compatible with the MS-Windows version of ZIP that is built-in.

Sorry if this isn't the help you wanted.

---

### Post by helpwiththerapture on 2024-09-22
I'm using them the way they always have worked, until very recently, GUI or command line, by default links for zip/7z/tar.gz were always backed up exactly as they should and they were restored the same way. A refresh install of Ubuntu 24.04.1 will work fine. Updating breaks it. This is something that has happened recently. The release version for 7z for example has jumped quite a bit.  Sorry if I was abrupt.

---


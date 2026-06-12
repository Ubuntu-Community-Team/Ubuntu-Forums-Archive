---
title: "Unable to unarchive tar backup"
date: 2008-02-14
forum: General Help
---

### Post by Elswood on 2008-02-14
Prior to doing a new install of Ubuntu Gutsy 32 bit, I backed up my home folder with konserve in kubuntu 64 bit.  This created a back-up tar file on my external hard drive.  Now, I can't get it to open.  I have tried "root" and double-clicked it.  Archive manager opens and begins to read the archive, but then finally I get this message:

tar: Removing leading `/' from member names
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Error exit delayed from previous errors

Can someone advise me how to read and unpack this archive?  I have tried reinstalling konserve but that didn't help any.  Is there some terminal commands that could allow me to access this data?  The drive is FAT32 and the tar file is over 3 gigs.  

Thanks for any help anybody can offer!

---

### Post by dannyboy79 on 2008-02-14
if it's a normal tar file, make a subfolder, put the tarball in there, then run this  command as root

tar -xvvf tarballnamehere

if it's a gzipped tarball (exmaple: foo.tar.gz) then run this command

tar -xvzf tarballnamehere

that should extract it if it's a valid archive otherwise it may be damaged and I can't help you with that.

---

### Post by astrotech226 on 2008-02-14
An easy way to tell what compression was used (if any) regardless of the filename or extension is with the "file" command.  From the command line, do this:

```
file tarballnamehere
```

Even if the extension doesn't show that it was gzip or bzip2 compressed, this will tell you type of decompression you need to be using.

---

### Post by Elswood on 2008-02-14
Thanks.  But it untarred only a few files before the same error message.  I will take the drive to work and see if the full file can be read by an Apple or Windows system.  I would like to get all the files back if possible.  Maybe it's not possible...

---


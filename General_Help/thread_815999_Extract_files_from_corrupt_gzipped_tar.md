---
title: "Extract files from corrupt gzipped tar"
date: 2008-06-02
forum: General Help
---

### Post by N2G(bn#7+ on 2008-06-02
Hi,

I have a .tar.gz file that has all my settings from my previous Ubuntu install in it. I want to unzip it but it seems to be corrupted in some way and I can't extract any of the files.

The error I get is:
```
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```
Can anyone help me recover the files?

Thanks,
Erland.

---

### Post by sdennie on 2008-06-02
Are you certain that you are using the command correctly?  To me that looks like the command is trying to read from stdin and not a file.

Edit:
Read a little closer.  Try:

```

tar xvf the_file.tar.gz

```

---

### Post by N2G(bn#7+ on 2008-06-02
Thanks. I was just doing it through the GUI, by opening or extracting it from Nautilus. After issuing your command in the terminal however, I get the same problem. It prints lots of files that are extracted then gets to
```
howden/.mozilla-thunderbird/1ke0b5qv.default/Mail/Local Folders/Sent
```
and prints:
```
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```

---

### Post by anxiousdog on 2008-11-26
Is it too late to resurrect this thread and see if there was ever a fix? I have the same problem and one of the folders I backed up is photos from a customer shoot and I *need* them! 

I don't want to extract the entire backup since it may cause some problems with my current install... Just need the photos! Help!

> gzip: stdin: unexpected end of file 
tar: Unexpected EOF in archive 
tar: Error is not recoverable: exiting now

---

### Post by trenthelms on 2009-08-01
Did anyone ever resolve this issue?  I have a similar problem.  I used sbackup to backup about 75 gigs of info.  There were five or so files created as part of the backup.  sbackup restore does not like the file.   It complains that the backup was in a earlier format.  And choosing to proceed didn't appear to work.   At least I can't tell that it did anything.   A peak of the first hundred lines or so in files.tgz appear to be gibberish.    Also looking at the ver file which should be text but it also looks like three or fous characters of gibberish.  I wonder if the file is really corrupt or if I'm looking at compressed data that somehow gunzip or tar or something else can't work with.   Anyway else seeing something similar?

---

### Post by penkoad on 2009-11-16
I have the exact same problem.

sbackup can no more restore my files. And when trying to extract manually the files.tgz archive.
It gives me the answer :

```

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

```

So so so uncool 	](*,)

---

### Post by Dorrax on 2009-12-06
I have this same problem. I have seen a post that says Fat32 filesystems typical of most USB/external HDs can't handle files larger than 4GB and creates a silent error, making you think you backed up your files instead of making a corrupted piece of crap.

---

### Post by trenthelms on 2010-01-17
Yep uncool for sure.  In my case I had formatted a USB drive with the EXT3 filesystem before running the backup.  I tested a smaller file, 35 gig, and that appeared to be okay.  It's when I added in someother including copies of virtual machines (many gigs) when I started having the problem.  Anyone seen a fix yet?  I'm holding onto my files.tgz in hope that someone has some magic for it.

---

### Post by xen2050 on 2012-08-23
Been looking for how to recover files from a corrupt tar file (compressed or not) and haven't found any answers yet aside from "transfer it again in binary mode" (no help) or "make it again correctly this time" (no help).

Have two ideas:

untar the file to recover the files up to the corrupted part, at least those should be good.

Try uncompressing the file to get a regular tar file, with a little luck that might skip over the corrupt part and uncompress the rest of the files (But the "unexpected EOF" suggests that there's no other files past this). After that, either try to untar the plain tar file, or try file/data carving tools to extract files, like using testdisk/photorec or similar. Some of the data carving tools might be able to uncompress the tar.gz file directly too so that's worth a try on it's own. Actually try that first, probably easier ;-)
Actually, if your tar.gz/tgz storage medium is the problem and it's giving the "unexpected EOF", then definitely try photorec on the whole disk, it should ignore the filesystem and read the disk directly and might be able to recover the tar.gz file or it's data better.

I'm surprised there aren't easy to find/working tar recovery programs, or if there are it's a well kept secret.

---

### Post by nothingspecial on 2012-08-23
Please start a new thread giving as much detail about your problem, what you have tried, and any errors you get. 
This thread is old. 
 
Closed.

---


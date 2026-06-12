---
title: "Backup On DVD`s (Span Discs)"
date: 2006-07-14
forum: General Help
---

### Post by CyberAngel on 2006-07-14
I've got a folder 10GB (And growing. I am storing all my Digital Photos there) on my Kubuntu. I'm looking for a solution that will let me backup to 4.7G DVD`s
e.g. fill one disc, tell me to put in another, etc, until all of the data is copied to disc(s).Is there any program that is able to do that job (Disc Spanning) for Linux?

---

### Post by mazirian on 2006-07-14
There are a lot of ways to approach this.  One of which is to use an archiving format that supports being split.  For example you could use plain old tar for this purpose.  It accepts a flag that will tell it to split the files into archives of a maximum size.  Obviously, an important feature for backing up to tape.  Please check the man page and test it first.  Other archival formats do this to.  cpio (i think) and others.  Rar is a nonfree archive that will also accomplish this.  Easiest would be to just divide the files between directories.  Ten you never need to worry about any problems restoring the archives.

---

### Post by CyberAngel on 2006-07-14
> **mazirian said:**
> ...Easiest would be to just divide the files between directories.  Ten you never need to worry about any problems restoring the archives.

That`s what I want because I want to be able to browse my files when they are on DVD. But I was asking if there was a tool to calculate automatically how many discs will be required and which files to enter on each disc until its maximum capacity.

---

### Post by mazirian on 2006-07-14
Oh!  Sorry.  I misunderstood.  Well, no, none that I am aware of.  Use du -hs directory to find a directory's size.  I suppose you could write a script of some sort to move the files until a given capacity is reached.  Sorry I was useless.

---

### Post by CyberAngel on 2006-07-14
> **mazirian said:**
> Oh!  Sorry.  I misunderstood.  Well, no, none that I am aware of.  Use du -hs directory to find a directory's size.  I suppose you could write a script of some sort to move the files until a given capacity is reached.  Sorry I was useless.

You were not useless :)
Thanks for the reply.

I will try write a bash script for the above job to create dirs of 4.3GB from the source you are giving it (If it is above 4.3 GB).

---

### Post by jeffus_il on 2008-01-05
You can use an archiver tool like rar or KArchiver to create a split archive to the size of your DVD, this requires temporary disk space  to build the split archive , also the disks are not readable straight from the drive. To make the disks readable, you need to split up the music yourself by directory. The easiest solution is to purchase an external USB2 drive for backing up to , their prices have come down a lot lately.

---

### Post by ozzymud on 2008-01-05
DiscSpan allows you to backup a directory of files to multiple DVDs on the Linux platform. If you had 20GB of photos, it would prompt you for 5 DVDs. It performs the backup at the file-level, meaning that a complete copy of each file is stored on a disc.

[http://sourceforge.net/projects/discspan](http://sourceforge.net/projects/discspan)

---

### Post by CyberAngel on 2008-01-05
> **ozzymud said:**
> DiscSpan allows you to backup a directory of files to multiple DVDs on the Linux platform. If you had 20GB of photos, it would prompt you for 5 DVDs. It performs the backup at the file-level, meaning that a complete copy of each file is stored on a disc.

[http://sourceforge.net/projects/discspan](http://sourceforge.net/projects/discspan)

Thank you very much :)

This is exactly what I was searching for!

---


---
title: "Deja Dup backup file location"
date: 2014-08-07
forum: General Help
---

### Post by RogerDavis on 2014-08-07
I'm considering using Deja Dup, but there are questions that I can't find clear answers to:

1) Where are the backup files saved in the cloud now that Ubuntu One is gone?
  
2) Can I direct it to use DropBox?

3) A USB drive?

4) Is there a site that has a CURRENT, FULL explanation of what goes on and operating controls?

5) Can it be used to do a full drive backup - as in restore to a new drive like an image, OS and all, start and run?

---

### Post by TheFu on 2014-08-07
I don't know the answer and don't use dejadup, but can provide some hints on where to find them.

4 - the [man page for deja-dup]("http://manpages.ubuntu.com/manpages/lucid/man1/deja-dup.1.html") should explain everything. It will show the options, what each means. DejaDup is a GUI over duplicity, so that may be a better manual page to read.  Duplicity can encrypt backups and store them on S3, FTP, rsync, and any storage mounted to the source system.  YOU control that.

1 - YOU tell any backup software where to be stored - which means the protocols available between the local machine and the remote machine should be all you worry about.  If dropbox supports ftp, rsync, or any of the protocols supported by the backup software, great.

3 - if you mount the USB drive, then it should write there.  However, the file system on the USB drive may be a limiting factor.

5 - DejaDup is NOT an image backup solution.  If you want to mirror a drive, there are many other tools for that. [http://ubuntuguide.org/wiki/Ubuntu_Trusty_System_Backup](http://ubuntuguide.org/wiki/Ubuntu_Trusty_System_Backup) will provide leads.  If you plan to move the HDD to a different system, there can be other complexities which prevent this from working now - mainly UEFI/Legacy BIOS boot and udev devices for networking (which is a minor issue).  I have moved BIOS boot HDDs many, many, many times between very different systems and that works. I've never moved a UEFI boot HDD - not once - so I don't know if that is trivial or very difficult.  I'd use ddrescue to image bit-for-bit from drive A to drive B.  However, if I want an image "backup", I'd use fsarchive, clonezilla, or partimage - these store all the information, but in a compressed format, without empty space.  fsarchive and resize during a restore should the target HDD be larger or smaller, but still have enough room for the data.

I hope all this makes sense and it helpful.

---


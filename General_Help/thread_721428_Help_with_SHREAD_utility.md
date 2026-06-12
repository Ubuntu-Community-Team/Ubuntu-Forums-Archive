---
title: "Help with SHREAD utility"
date: 2008-03-11
forum: General Help
---

### Post by am91962 on 2008-03-11
Hi, I'm fairly new to linux/ubuntu and need some help understanding shread.  I'm trying to use it to wipe the empty space of my hard drive.  I use the command sfill /home.  The problem is I don't think it works, I left it running for about ten hours and it still hadn't given me a message about it being finished.  Should it normally take that long to wipe the free space?  Is there something I should be doing differently?

Thanks

---

### Post by justleen on 2008-03-11
can you ginve some more details on the tool you used?

I know "shred "  comes default, but i dont know "shread".

depening on the disk size, and the amount of times the tool rewrites/fills the disk and blocksize of the disk, it can take quite a while, yes.

---

### Post by niteshifter on 2008-03-11
@ am91962: Tools like sfill (part of a toolkit from thc.org, IIRC) are quite old and may not be doing what you think they are. That tool (sfill) pre-dates the ext3 filesystem and cannot deal with journaling, for example.

I'm with justleen: I know shred but do not know "shread". shred will not do what you want (clear the slack space on a hard drive). It will overwrite a file beyond the file's length, wriing data to fill the tail block of disk storage used by the file.

I'll also mention that experience learned on M$ filesystems (FAT versions, NTFS) don't translate well into the Linux world. Putting the pieces of a file back together on a Linux box is very difficult, won't be complete (unless the attempt to reconstruct occurs immediately after unlinking the file from the filesystem, any delay: the system is re-using blocks with each tick of the clock).

OTOH, use of journalling filesystems complicate matters. The default on Ubuntu is ext3 in data-ordered mode (which means shred will work on the data, the last pass on metadata alteration remains). Setting up a system to use ext3 in "journal mode" makes shred ineffective.

If secure file storage is what you are after you've basically two choices: Full Disk Encryption (via dm-crypt) or use Truecrypt. Of the two I wouldn't wish FDE on anybody (you trade problems: file security management becomes key management, backup is more problematic). Truecrypt works well, one can place any filesystem (journalled or not) on a TC volume, TC volumes have no signature, they appear to be random data, a TC "container" can be a file or a device (like a USB drive or SD card).

---

### Post by am91962 on 2008-03-11
Sorry for my typo, I wrote this a little early in the morning, I did mean Shred.  Thanks for the help.  One quick question, I have deleted a couple word docs and programs in the past, and I need to make sure they're gone, is there a program that will write over the free space?

Thanks

---


---
title: "How to ensure that deleted files are completely deleted?"
date: 2007-07-26
forum: General Help
---

### Post by Gadren on 2007-07-26
I've deleted some sensitive files, and emptied the trash.  I probably shouldn't have emptied the trash before using a shred program.  How can I make sure that these files are reasonably irretrievable?

---

### Post by nichipet on 2007-07-27
I don't know about ensuring it now, but in the future use shred. From a prompt, take a look at

```
man shred
```

---

### Post by HermanAB on 2007-07-27
Note that I do military work, so I do know something about this problem.

The short answer is: You cannot delete sensitive files.

Shredder and repeated erase utilities are just smoke and mirrors - they don't work.  One reason being that Ext3, the default Ubuntu file system is a logging file system, so it never overwrites anything (Until it reaches the end of the disk and starts at the beginning again!).  So if you overwrite a file any number of times, the original is still untouched and all you have done is waste your time.

The longer answer is here: 
[http://cmrr.ucsd.edu/Hughes/subpgset.htm](http://cmrr.ucsd.edu/Hughes/subpgset.htm)
[http://cmrr.ucsd.edu/Hughes/SecureErase.html](http://cmrr.ucsd.edu/Hughes/SecureErase.html)

Using the utility built into all modern disk drives, you *can* erase the whole disk drive, but you cannot erase a single file only.

Basically, the only way to securely erase files, is to use an encrypted file system and encrypt your disk drive before you write anything to it.  Read up on dm-crypt:
[http://www.saout.de/misc/dm-crypt/](http://www.saout.de/misc/dm-crypt/)

'Hope that helps!

Herman

---

### Post by Espreon on 2007-07-27
The only secure way to do thing on an Ext3 fs is to put all sensitive data on a TC container, I suppose.

---

### Post by HermanAB on 2007-07-27
Actually, the only way to securely erase a file on a HDD is with a welding torch, but a workout with a 25lb sledge hammer followed by a trip to the local river is also reasonably secure.

---

### Post by Gadren on 2007-07-27
OK, thanks anyway.  It's not like uber-top-secret government or company stuff... just personal files I was a little concerned about.

---

### Post by atlfalcons866 on 2007-07-27
from wikipedia

File wiping on journaling file systems

Many modern operating systems such as Windows XP (NTFS), Mac OS X (HFS Plus), and GNU/Linux with a kernel version greater than 2.4 (ext3, JFS, ReiserFS, and XFS) have the ability to use a journaling file system that makes complete erasure of data unlikely. Journaling file systems are used to increase the integrity of data in case of failures. To accomplish this, the file systems keep metadata and logs in various places known to the file system; most file systems can also journal all data, but turn this functionality off by default. The metadata and logs will not be securely wiped with a file wiping tool. To increase performance, these file systems will often arrange I/O commands in an efficient manner and may continuously move data around the disk to prevent the need for operations similar to Windows Disk Defragmenter. The performance enhancing capabilities of the file systems makes wiping files hard because the data may only be wiped in its present location, leaving unwiped blocks of the data in other locations on the hard disk. Also, the file system may not execute all requests of a redundant I/O command.

There are several ways to securely wipe files when using journaling file systems:

   1. Store data that needs to be wiped on a partition (slice, volume, or drive) that uses a non-journaling file system. For example, users of Windows can use a Z: drive formatted with FAT32, and users of GNU/Linux can use a partition formatted with ext2.
   2. Store data that needs to be wiped on a partition or disk that uses disk encryption. This eliminates the need to use a secure wiping mechanism for individual files, however, future attacks against the disk encryption suite might make this less desirable.
   3. Store data on a temporary partition using any journaling or non-journaling file system. When it is time to wipe all files, use a tool such as Eraser or Wipe to securely wipe the entire partition.
   4. Physically destroy the hard drive after use by melting the hard drive. (Passing a magnet over the hard drive will not work; the metal casing acts as a magnetic shield.)
   5. On ext3, set the journal mode to ordered data mode (the default for newer versions). In ordered mode, ext3 only journals metadata, not actual data. To find out if you are using ordered data mode, type 'dmesg | grep ordered' (on a Debian GNU/Linux system) and look for a message saying that the partition has been mounted ordered data mode.

---


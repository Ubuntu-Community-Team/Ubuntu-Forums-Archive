---
title: "Recovering partition with TestDisk."
date: 2012-12-28
forum: General Help
---

### Post by ByaTsuke on 2012-12-28
So I suffered from an unfixable WIndows 8 problem which wasn't even fixable by recover disk. 

So I installed Ubuntu on my portable HDD, so now I am currently on Ubuntu.
I installed Testdisk to recover my old files. 

I ran Testdisk, analyzed it and wrote my partition table? I believe thats what it was called.  Can anyone tell me what that is about? what did it really do?

So here is what is inside my original HDD :

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

     Partition                  Start        End    Size in sectors
> 1 * HPFS - NTFS              0  32 33  2349 223 50   37748736 [PQSERVICE]
  2 P HPFS - NTFS           2349 223 51  2362 159 37     204800 [SYSTEM RESERVED
  3 P HPFS - NTFS           2362 159 38 54274  26 24  833957888
  4 E extended LBA         54274  27  1 60801 254 63  104870619
  5 L HPFS - NTFS          54274  58 57 60801  47 46  104855552 [Local Disk]


3rd partition is basically my Local Disk C where all my files are there even the windows 8 OS. 

You can just ignore 5th since it's a partition I made on my own to store some backups. 

Rest of them are I believe were created automatiaclly by default, not sure if I am suppose to delete them? or should I not?

Basically, I am just trying to reinstall windows 8, by recovering all the files from USER and then format it and install Windows 8 again.

---

### Post by oldfred on 2012-12-28
The pqservice is your Vendor recovery. Did you make a full DVD set to be able to restore system to as purchased? Otherwise without that partition you may not be able to restore system, even if booting other systems.

It looks like you have boot flag on sda1 which is vendor recovery. Windows has a (hidden in Windows) 100 to 200MB boot/repair partition which looks like sda2 or system reserved. That partition should have boot flag for Windows to boot. And f8 when booting that partition should get you into the Windows recover or repair console.

Then your main install is in sda3 and a deeper search with testdisk should show all your files. Backup anything not backed up if reinstalling.

---

### Post by ByaTsuke on 2012-12-28
> **oldfred said:**
> The pqservice is your Vendor recovery. Did you make a full DVD set to be able to restore system to as purchased? Otherwise without that partition you may not be able to restore system, even if booting other systems.

It looks like you have boot flag on sda1 which is vendor recovery. Windows has a (hidden in Windows) 100 to 200MB boot/repair partition which looks like sda2 or system reserved. That partition should have boot flag for Windows to boot. And f8 when booting that partition should get you into the Windows recover or repair console.

Then your main install is in sda3 and a deeper search with testdisk should show all your files. Backup anything not backed up if reinstalling.

Thanks, for the response.

I have a bootable USB, windows 8 install/repair menu does boot from the usb, but again it just freezes, I literally tried everything, so the only thing I could do now is boot a separate OS installed on my USB and grab my files then format my Local Disk drive and install windows 8 freshly. 

I don't need to do deep search because I can already list files, and see them. So I am just wondering how do I copy them, and how will I be able to format the drive whilst fixing errors if there's any alongside?

Then I'll boot windows 8 iso on my other usb and freshly install it. That's kind of my plan atm.

I was wondering what partition table really is, what is it's purpose? Because I analyzed the disk, and wrote a partition table because the instructions I saw online told me saw, but I don't see what it did?

---

### Post by oldfred on 2012-12-28
Both the older MBR(msdos) and newer gpt(GUID) partitioning schemes for hard drives have partition tables. The table lists the start & size of each partition on the hard drive and what format it is.

       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

            [http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

The first part of a MBR is boot code and the last part of the MBR is the partition table.

Windows also have information in its PBR or partition boot record on start & size of partition which must be the same as the partition table or Windows does not work.
While more Vista, still applies to current Windows with MBR.
       
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---


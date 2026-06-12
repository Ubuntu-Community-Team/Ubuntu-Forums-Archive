---
title: "Format FAT32 drive"
date: 2008-01-12
forum: General Help
---

### Post by timboellis on 2008-01-12
I have a FAT32 external HDD however in FAT which has all my MP3's , docs etc. if I was to change ti to Linux whatever that is Resizer or? will it speed up a lot or not much.

And is there a way to format it without formatting it if you are with me or in other workds wihtout having to backup all my data ?

---

### Post by hardyn on 2008-01-12
not totally sure what you are asking?

but if you have the drive external, i assume that you might pack all of your stuff around with you.  I would just leave it as FAT, then you know it will work on windows and apple boxes.

speed improvement, maybe, but being external you are limited by the size of the pipe anyway; althought the other file systems are more spacially efficient.  there are some tools to replace the file systems (windows had a tool to change fat to fat32), but generally you must reformat.

---

### Post by timboellis on 2008-01-12
Well yes I have a drive to carry about it was my 500g drive but now I have another 40 gig drive that I can use just for pc repairs and load the software on that.

So was looking at reformatting my 500g to Linux if it would improve the speed and the relability of it.

---

### Post by -grubby on 2008-01-12
do you mean reformatting your 500GB drive to a linux file system? Or installing linux on it? If you want to format it to a linux filesystem you will have to backup your files on it. And it won't work in windows unless you install read/write support for [whatever filesystem you use on it]

---

### Post by erpo on 2008-01-12
Yes, using the ext3 filesystem (or another filesystem with journaling) will improve your filesystem's reliability over FAT32.

Yes, you can convert from one filesystem to another without necessarily losing all of your files in the process. Here is the process:
1. Shrink the FAT32 partition to as small as you can get it.
2. Create a new ext3 partition in the free space.
3. Copy all of the files you can from the now completely stuffed FAT32 filesystem to the empty ext3 filesystem.
4. Shrink the now somewhat empty FAT32 filesystem to as small as you can get it.
5. Expand the ext3 filesystem as much as you can.
6. Go to step 3.
**WARNING WARNING WARNING**: This is a risky procedure. If the power never goes out and all of the tools work like they should, everything will work out fine. If the power goes out or a tool has a bug in it, **you could lose part or all of your data**.

Yes, you can mount ext3 filesystems in Windows (and probably Mac), but the necessary drivers are a gamble. For some people they work fine. For others (like me) they cause data loss and crashes.

In conclusion, you would be a fool to convert your drive from FAT32 to ext3. If you really want a lot of HDD space that's reliable and accessible, do what I did and build a home server with RAID, samba, and sftp. You can't carry it around with you in your pocket, but after carrying around a 500GB drive in an external USB enclosure for a while and then looking at the SMART stats on it, I'm convinced that's a bad idea anyway.

---


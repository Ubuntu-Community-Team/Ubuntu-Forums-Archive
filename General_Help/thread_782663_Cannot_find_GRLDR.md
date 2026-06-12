---
title: "Cannot find GRLDR"
date: 2008-05-05
forum: General Help
---

### Post by owen22 on 2008-05-05
Hi,
   I have installed wubi and then went to reboot into ubuntu but i get an error message (Windows XP, Dell Dimension 5100)

Cannot find grldr on all devices press ctrl+alt+delete to restart

I have had a look through the forums but cannot seem to get any help. If a solution could be posted in simple terms I would appreciate it.

Thanks

---

### Post by ago on 2008-05-05
Do you see wubildr and wubildr.mbr in any of your drives? It might be they were copied on the wrong drive. Try to copy them onto the boot drive.

---

### Post by owen22 on 2008-05-05
The wubildr and wubildr.mbr files are on my hard drive C:/. Is the boot drive my newly created ubuntu partition? I copied the files into C:/ubuntu/disks/boot/grub

Then restarted but I had the same problem

---

### Post by ago on 2008-05-05
> **owen22 said:**
> The wubildr and wubildr.mbr files are on my hard drive C:/. Is the boot drive my newly created ubuntu partition? I copied the files into C:/ubuntu/disks/boot/grub

Then restarted but I had the same problem

The files have to be in C:\
You can press INSERT rapidly at boot as soon as you select "Ubuntu". 
Let me know if you see any interesting message

---

### Post by owen22 on 2008-05-05
> **ago said:**
> The files have to be in C:\
You can press INSERT rapidly at boot as soon as you select "Ubuntu". 
Let me know if you see any interesting message

I tried pressing INSERT but no messages came up. The screen carried on as usual and then i got the GRLDR message again

---

### Post by ago on 2008-05-05
Remove ANY file called grldr* or wubildr* or menu.lst from all your drives. Then uninstall Wubi and reinstall. What wubi version did you use by the way?

---

### Post by tinybit on 2008-05-05
Copy wubildr to all drives(the root dir) and try again.

List your filesystem types, and partition sizes, please.

And is your XP with SP2 or SP3?

Also a screen shot please.

@ago

If grldr not found, then the Insert key will not function.

Even if GRLDR is in C:, it still possible that it is not accessible by BIOS. This is because some BIOSes have the 137G-limit BUG.

We need a tool like "defrag" to place wubildr in the beginning 137G of the disk physically.

---

### Post by owen22 on 2008-05-05
I used the latest version of Wubi 8.04.501

---

### Post by ago on 2008-05-05
> **tinybit said:**
> If grldr not found, then the Insert key will not function.
Yeah i realized that (ex post) :)
I think there might be some "left over"

---

### Post by owen22 on 2008-05-05
Ok I have removed ANY file called grldr* or wubildr* or menu.lst and re-installed Wubi but no luck.

I am using XP sp2 and I have alocated Wubi 10Gb of disk space.

When you say "Copy wubildr to all drives(the root dir)" do you mean into C:/ and the C:/ubuntu folders. I have checked and wubildr is in C:/ and C:/ubuntu/winboot

Also how do I get a screenshot of the screen when I reboot and select Ubuntu and then get the GRLDR error?

---

### Post by tinybit on 2008-05-05
How many disks and partitions do you have?

And what is the size for each?

And what are the filesystem types, say, FAT32 or NTFS?

And about the screen shot, you may write it down on a paper and then post it here.

"Copy wubildr to all drives(the root dir)" means copy wubildr to the ROOT directory of ALL partitions on ALL your disks, in other word, to C:\ and D:\ and E:\ and so on.

---

### Post by owen22 on 2008-05-05
As far as I am aware i don't have any partitions on the drive (other than the one created for wubi to install ubuntu)

The filesystem type is NTSF

wubildr is on the C:/ and in C:/ubuntu/winboot

The error message I get after rebooting and selecting to start Ubuntu OS is:

Try (hd0,0) : FAT16: No WUBILDR
Try (hd0,1) : NTSF5: 2
Try (hd0,2) : FAT32: No WUBILDR
Try (hd0,3) : invalid or null
Try (fd,0)  : invalid or null
ERROR: Cannot find GRLDR in all devices: Press ctrl+alt+delete to restart

Thanks for helping out

---

### Post by bean123 on 2008-05-05
It seems grldr.mbr has problem reading grldr from ntfs partition, please use fstest.exe to gather more information:

fstest info C:\
fstest inode C:\wubildr
fstest comp C:\wubildr

---

### Post by owen22 on 2008-05-05
How do I use fstest.exe?

---

### Post by bean123 on 2008-05-05
Download it from:

[http://grub4dos.sourceforge.net/grub4dos](http://grub4dos.sourceforge.net/grub4dos)

It's a command line tool for windows 2k/xp.

---

### Post by owen22 on 2008-05-05
hmm, i have downloaded fstest.exe but i'm still not sure how to use it?

---

### Post by bean123 on 2008-05-05
1, Inside Windows, run cmd.exe to start command line
2, use cd to change to the directory of fstest.exe, for example, if you copy fstest.exe to C:\, then

cd C:\

3, Enter the following commands, paste the result here:

fstest info C:\
fstest inode C:\wubildr
fstest comp C:\wubildr

---

### Post by owen22 on 2008-05-05
Okay i gave it a go, I thought ubuntu was supposed to be easy to install:)

C:\>fstest info C:\
Non-resident attribute list too large
version: 1.0 build 2
part_base: 0x17886 (47M)
part_leng: 0x1CB880AA (235280M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x627E90

C:\>fstest inode C:\wubildr
Non-resident attribute list too large
Run list overflow
Read MFT 0x16A13 fails
ntfs_dir: 17

C:\>fstest comp C:\wubildr
Non-resident attribute list too large
Run list overflow
Read MFT 0x16A13 fails
ntfs_dir: 17

C:\>

---

### Post by bean123 on 2008-05-05
This indicates that your C: drive is too fragmental, try to defrag the partiton.

---

### Post by bean123 on 2008-05-05
@owen22:

I just upload a new version of fstest.exe at the same address, it shows the exact size of your non-resident attribute list, please rerun the above commands and paste the result.

---

### Post by owen22 on 2008-05-07
Ok I ran a disk defrag and downloaded the new fstest.exe Here are the results:

C:\>fstest info C:\
Non-resident attribute list too large
version: 1.0 build 2
part_base: 0x17886 (47M)
part_leng: 0x1CB880AA (235280M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x627E90

C:\>fstest inode C:\wubildr
Non-resident attribute list too large
Run list overflow
Read MFT 0x16A13 fails
ntfs_dir: 17

C:\>fstest comp C:\wubildr
Non-resident attribute list too large
Run list overflow
Read MFT 0x16A13 fails
ntfs_dir: 17

---

### Post by tinybit on 2008-05-07
> **bean123 said:**
> @owen22:

I just upload a new version of fstest.exe at the same address, it shows the exact size of your non-resident attribute list, please rerun the above commands and paste the result.

> **owen22 said:**
> Ok I ran a disk defrag and downloaded the new fstest.exe Here are the results:

C:\>fstest info C:\
Non-resident attribute list too large
version: 1.0 build 2
part_base: 0x17886 (47M)
part_leng: 0x1CB880AA (235280M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x627E90

C:\>fstest inode C:\wubildr
Non-resident attribute list too large
Run list overflow
Read MFT 0x16A13 fails
ntfs_dir: 17

C:\>fstest comp C:\wubildr
Non-resident attribute list too large
Run list overflow
Read MFT 0x16A13 fails
ntfs_dir: 17

This result is exactly the same as the previous one, even for the version number 1.0 build 2:

> **owen22 said:**
> Okay i gave it a go, I thought ubuntu was supposed to be easy to install:)

C:\>fstest info C:\
Non-resident attribute list too large
version: 1.0 build 2
part_base: 0x17886 (47M)
part_leng: 0x1CB880AA (235280M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x627E90

C:\>fstest inode C:\wubildr
Non-resident attribute list too large
Run list overflow
Read MFT 0x16A13 fails
ntfs_dir: 17

C:\>fstest comp C:\wubildr
Non-resident attribute list too large
Run list overflow
Read MFT 0x16A13 fails
ntfs_dir: 17

C:\>

@owen22

Are you sure you were running the newer one?

---

### Post by owen22 on 2008-05-07
Yer i'm pretty sure I was running the new one, I the link and clicked fstest.exe

---

### Post by bean123 on 2008-05-07
The new version didn't output message "Non-resident attribute list too large" , I guess you must be using the old one, perhaps your web browser cache the previous result or something.

Anyway, I upload it again with a new name, please try again:

[http://grub4dos.sourceforge.net/grub4dos/fstest_1.exe](http://grub4dos.sourceforge.net/grub4dos/fstest_1.exe)

---

### Post by owen22 on 2008-05-08
ok I have just tried the latest build, here are the results - 

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\>fstest info C:\
Non-resident attribute list too large (6656)
version: 1.0 build 2
part_base: 0x17886 (47M)
part_leng: 0x1CB880AA (235280M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x627E90

C:\>fstest inode C:\wubildr
Non-resident attribute list too large (6656)
ntfs_dir: 17

C:\>fstest comp C:\wubildr
Non-resident attribute list too large (6656)
ntfs_dir: 17

---

### Post by bean123 on 2008-05-09
Please try the new version at:

[http://grub4dos.sourceforge.net/grub4dos/fstest.exe](http://grub4dos.sourceforge.net/grub4dos/fstest.exe)

The first line of the info command should be:
version: 1.0 build 3

If it isn't, then you must be downloading the old version, try to clear the browser cache and download again.

---

### Post by ago on 2008-05-09
bean123, you might want to put the version in the filename, to avoid any caching problem...

---

### Post by nik_nah on 2008-11-02
I had the "FAT32: No WUBILDR" problem too.
Here's how I fixed it...
In windows the C: drive doesn't have to be the first drive in the disk.
You can map it to whatever, my drives went like this...
D: = hd(0,0)  FAT32
C: = hd(0,1)  NTFS

But the ubuntu installer puts the wubildr files into C: which was really the 2nd partition and grub couldn't find it.
So I copied the wubildr files to D:\ and it worked.

hope this helps someone.

---

### Post by sudhi1987 on 2010-08-31
Hi  ,
i have the same problem while booting ubuntu saying 
try (hd0,0):FAT16 : No WuBILDR
try (hd0,1):NTFS5 : No WuBILDR
try (hd0,2):NTFS  : No WuBILDR
ERROR : Cannot find GRLDR in all devices : Press ctrl+alt+del to restart

I followed instructions in this  thread , installed new fstext.exe and i have results as below
E:\>fstest.exe
Usage:
  fstest [-q] [-v[n]] info pathname
  fstest [-q] [-v[n]] list pathname
  fstest [-q] [-v[n]] blocklist pathname
  fstest [-q] [-v[n]] comp filename [offset] [length]
  fstest [-q] [-v[n]] [-b] dump filename [offset] [length]
  fstest [-q] [-v[n]] [-b] inode filename

E:\>fstest.exe --help
Invalid option

E:\>fstest.exe --?
Invalid option

E:\>fstest info e:/
version: 1.0 build 3
part_base: 0xEB2C800 (120409M)
part_leng: 0xE67B800 (118007M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

E:\>fstest inode e:\ubuntu\winboot\wubildr
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=80)
    wubildr
  $DATA (0x80) (nr,sz=197915)
    2230552+392
Warning: reading beyond the 137G limit

E:\>fstest comp e:\ubuntu\winboot\wubildr
File size : 197915
Comparing
Succeed
Warning: reading beyond the 137G limit

E:\>


What is the next step i have to do to recover my ubuntu.


Thanks

---

### Post by Wim De Winter on 2011-01-15
OK, same error messages here on my wifes Vaio. Output of the requested information:

```
Microsoft Windows XP [versie 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\>fstest info c:\
version: 1.0 build 3
part_base: 0xFD778A (8110M)
part_leng: 0x6FC3DBF (57223M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

C:\>fstest inode c:\wubildr
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=48)
  $FILENAME (0x30) (r,sz=80)
    wubildr
  $SECURITY_DESCRIPTOR (0x50) (r,sz=80)
  $DATA (0x80) (nr,sz=88171)
    21600608+176

C:\>fstest comp c:\wubildr
File size : 88171
Comparing
Succeed
```

Defragmenting now...

---

### Post by bcbc on 2011-01-15
This thread is a couple of years old. You might not get the response you hope for. Probably better to create a new thread, and describe in detail your problem, symptoms, what you might have done to cause it, and the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results will help too.

PS. Make sure you have a c:\wubildr file - if not copy it from c:\ubuntu\winboot\wubildr (change drive letter if required).

---

### Post by Wim De Winter on 2011-01-16
Well actually, just finished defragmenting in winxp and this solved the problem for now, so it seems :confused: Thanks anyway!

---

### Post by bcbc on 2011-01-16
> **Wim De Winter said:**
> Well actually, just finished defragmenting in winxp and this solved the problem for now, so it seems :confused: Thanks anyway!

Well, that's good to hear!

---

### Post by nagarjunr on 2012-09-27
> **nik_nah said:**
> I had the "FAT32: No WUBILDR" problem too.
Here's how I fixed it...
In windows the C: drive doesn't have to be the first drive in the disk.
You can map it to whatever, my drives went like this...
D: = hd(0,0)  FAT32
C: = hd(0,1)  NTFS

But the ubuntu installer puts the wubildr files into C: which was really the 2nd partition and grub couldn't find it.
So I copied the wubildr files to D:\ and it worked.

hope this helps someone.

Hi thank you soooooooo much....atlast after a day of hardship im running ubuntu 12.04 alongside windows 7. Its just because of your post. I just copied those files from C: into E: drive in which i had installed ubuntu.once again thank you.:D:D

---

### Post by oldos2er on 2012-09-27
Closed. Please don't bump old threads.

---


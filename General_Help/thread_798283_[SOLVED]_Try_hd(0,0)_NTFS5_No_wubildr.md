---
title: "[SOLVED] Try hd(0,0): NTFS5: No wubildr"
date: 2008-05-18
forum: General Help
---

### Post by help_me_please on 2008-05-18
that is the msg i get when trying to boot ubuntu. after approx 1 minute, the msg disappears and the system boots normaly, but it's a tremendous bother. i have wubildr & wubildr.mbr in C:\ and in C:\ubuntu\winboot\. i tried reinstalling wubi. i ran chkdsk /r and everythings OK.

im running wubi 8.04 on vista home premium.

help me please.

---

### Post by veryofficial on 2008-05-18
Hi,
Even I have the same problem in Vista home premium edition installed in Dell inspiron. This is not encouraging because support for Vista should be expected as it is not some arcane OS.

---

### Post by ago on 2008-05-18
press insert rapidly after selecting "ubuntu" and report any error you may see.

---

### Post by help_me_please on 2008-05-18
i get some errors about MBR memory not being the same as bios memory definitions. would a bios update correct this problem?

---

### Post by help_me_please on 2008-05-18
sry for my earlier unhelpful post - i was in class and battery was running low.

here's what happened when i pressed a whole lot of insert:
* same 1 min. long "Try hd(0,0): NTFS5: No wubildr" msg.

* a few msgs flash on screen to fast for me to read (maybe because i didn't stop hitting insert)

* then i get this:
> hard drives: 1, int13:F0008090, int15:F000F859
get_diskinfo(80), int13/41(80), version=AA300005, int13/48(80), err=0, C/H/S=16/383/16/63, sector count/size=2344416480/0, int13/08(80), version=0, C/H/S=1024/171/40, int13/02(80), err=0,
warning: MBR cylinders(14594) is not equal to the BIOS one (16383)

warning: MBR heads(255) is not equal to the BIOS one (171)

warning: MBR total sectors(234452610) is greater than the BIOS one (234441648 )
some buggy BIOSes could hang when you access sectors exceeding the BIOS limit.
LBA, C/H/S=14594/255/63, sector count/size=234452610/512
boot drive=80, int13/4B01(80), err=1, drive=80, not CD
get_cdinfo(7F), int13/4B01(7F), err=1, drive=7F, cdrom_drive==FFFFFFFF
starting cmain() ... open/default ... failure

then i hit insert again and get into the grub menu and ubuntu boots ok.

im running wubi in vista on a 120GB HD no extra partitions, LG notebook.

---

### Post by tinybit on 2008-05-18
> 
Try hd(0,0): NTFS5: No wubildr


Don't care about this message too much since you can enter the grub environment normally.

I only wonder which wubildr was found and booted to the grub environment? where is it? Is it from your USB key or diskette?

---

### Post by help_me_please on 2008-05-18
i have no usd device plugged in (other than a mouse) and no CD's nor diskettes in drive.

---

### Post by bean123 on 2008-05-19
In the grub menu, press 'c' to enter console, then enter the following command:

cat (hd0,

followed by [TAB] key (no <ENTER> in-between), this will list all the partitions in your hard disk. The reason to do this is that sometime they put in hidden partition in notebook, this would show them all.

Also, when you are inside vista, use the fstest.exe to gather information about the ntfs partition:

fstest.exe info C:
fstest.exe list C:\
fstest.exe inode C:\wubildr
fetest.exe comp C:\wubildr

You can download fstest.exe from:

[http://grub4dos.sourceforge.net/grub4dos/](http://grub4dos.sourceforge.net/grub4dos/)

---

### Post by tinybit on 2008-05-19
you may also try to delete c:\wubildr(or rename it) and reboot, and see whether or not grub could be booted.

---

### Post by help_me_please on 2008-05-19
cat (hd0, [TAB] showed that i have 2 partitions of type ntsf. im assuming that the problem is that wubi is attempting to load from partition 0 while it is actually in partition 1. what do i have to edit to correct this?

just in case, here is the info from ftest.exe:

> fstest info C:\

version: 1.0 build 3
part_base: 0x200800 (1025M)
part_leng: 0xDD93800 (113447M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

fstest list c:\

list of folders & files in c: with hexa num's in the left column. wubildr and wubildr.mbr exist

wubilder hex value: 00001348 size: 186463
wubildr.mbr hex value: 0000134F size: 8192

fstest inode c:\wubildr

Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=80)
    wubildr
  $DATA (0x80) (nr,sz=186463)
    13690352+368

fstest comp c:\wubildr

Filesize: 186463
comparing
succeed

---

### Post by bean123 on 2008-05-19
> **help_me_please said:**
> cat (hd0, [TAB] showed that i have 2 partitions of type ntsf. im assuming that the problem is that wubi is attempting to load from partition 0 while it is actually in partition 1. what do i have to edit to correct this?

just in case, here is the info from ftest.exe:

It's actually all right. The first partition is a vendor reserved partition,     which correspond to the hd(0,0): NTFS5: No wubildr line. The second partition is your main partition. grldr DOES load properly, although there might be some efficiency issue.

If I guess right, your primary MFT is stored in non resident attribute list, you can verify it with:

fstest.exe inode C:\$MFT
fstest.exe inode C:\.

---

### Post by help_me_please on 2008-05-19
sorry dude, but i only understood about half of what you said...:? could you repeat that in english please :P

i ran the fstest's u suggested, but i couldn't make heads of tails of the output.

---

### Post by ago on 2008-05-19
Can you paste the output here?

---

### Post by help_me_please on 2008-05-19
output from fstest:

> fstest inode c:\

ntfs_dir: 17

fstest inode c:\$MFT
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=132317184)
    6291456+113280,118847360+7040,121304912+46224,148591136+47360,22049112+44528

  $BITMAP (0xB0) (nr,sz=16152)
    6291448+8,116169752+8,12540896+8,13641128+8

---

### Post by bean123 on 2008-05-19
what is the result of

fstest.exe inode C:\.

---

### Post by help_me_please on 2008-05-19
ntfs_dir: 17

---

### Post by bean123 on 2008-05-19
What about

fstest.exe inode C:\#5

---

### Post by help_me_please on 2008-05-19
output of fstest inode c:\#5

> 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=68 )
    .
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=20480)
    1843264+8,133022392+8,133023112+8,118816+16
  $BITMAP (0xB0) (r,nm=$I30,sz=8 )
  $UNKNOWN (0x0) (r,nm=$TXF_DATA,sz=56)


---

### Post by bean123 on 2008-05-19
Thanks for your feedback, I figure it out now. Vista create a huge non resident root directory with only a handful of files, which cause grldr.mbr to load many useless sectors. I fixed this once in the ntfs driver. Unfortunately, grldr.mbr is already too crowded, there is no room for extra code, so can't fix it here.

But there is another option. IIRC, vista support boot file up to 32K, which is enough for a grub2 core.img. If we use grub2, we can skip the real mode loader grldr.mbr and load the kernel directly.

---

### Post by help_me_please on 2008-05-19
so if i replace the vista boot file with the grub boot file the "Try hd(0,0): NTFS5: No wubildr" error will stop? might as well get rid of the wubi and install ubuntu on seperate partition...

by the by, is there a way to save all updates, packages and configurations of wubi and apply them to a clean install?

---

### Post by ago on 2008-05-19
You can try [https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da](https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da)

But the code is recent and has not been fully tested yet

---

### Post by help_me_please on 2008-05-19
tahnx a bunch guyz. you've been a great help.

---

### Post by tinybit on 2008-05-19
> **bean123 said:**
> Unfortunately, grldr.mbr is already too crowded, there is no room for extra code, so can't fix it here.


It seems this is not the case. Though grldr boot code has only a 16-sector room, grldr.mbr could have a size of up to 63 sectors. So grldr.mbr can be fixed and there is no difficulty in principle.

Another point,
> 
$MFT
$DATA (0x80) (nr,sz=132317184)
6291456+113280,118847360+7040,121304912+46224,1485 91136+47360,22049112+44528


Though MFT is as large as 132MB, but can we only read the required portion for wubildr? If possible, this could save time.

---

### Post by bean123 on 2008-05-20
> **tinybit said:**
> It seems this is not the case. Though grldr boot code has only a 16-sector room, grldr.mbr could have a size of up to 63 sectors. So grldr.mbr can be fixed and there is no difficulty in principle.

Right, but we also need to maintain compatibility with xp, which doesn't support boot file larger than 8K.


> 
Though MFT is as large as 132MB, but can we only read the required portion for wubildr? If possible, this could save time.

It'd quit scanning as soon as wubildr is found, but obviously, vista put it somewhere at the end, so it has to go through the whole unused blocks.

---

### Post by tinybit on 2008-05-20
> **bean123 said:**
> Right, but we also need to maintain compatibility with xp, which doesn't support boot file larger than 8K.

At least our current grldr.mbr (of course in grub4dos I mean) has exceeded 8 KB. So patching to it will not produce new problems.

> **bean123 said:**
> 
It'd quit scanning as soon as wubildr is found, but obviously, vista put it somewhere at the end, so it has to go through the whole unused blocks.

According to this, we simply can not produce a patch to resolve this issue. Can we think so?

Consider we can not skip those garbage sectors in MFT. So we cannot resolve this issue except when we put all the code into GRLDR.MBR(just as GRUB2 you mentioned above). Is that true?

---

### Post by bean123 on 2008-05-20
> **tinybit said:**
> At least our current grldr.mbr (of course in grub4dos I mean) has exceeded 8 KB. So patching to it will not produce new problems.

It's not just size. If we expand the ntfs boot sector, it would occupied 5 sectors, this would push the ext2 code backward. Although it's possible to handle this with some #ifdef's, but I'm not fond of conditional compilation. Also, it would break the linkage with grubinst as well.


> 
According to this, we simply can not produce a patch to resolve this issue. Can we think so?

Consider we can not skip those garbage sectors in MFT. So we cannot resolve this issue except when we put all the code into GRLDR.MBR(just as GRUB2 you mentioned above). Is that true?

There is a trick to solve this. We can use the $INDEX_ALLOCATION attribute to get a bitmap of currently used blocks. The ntfs driver in grub4dos and grub2 already have code to handle this situation.

---

### Post by tinybit on 2008-05-20
> **bean123 said:**
> It's not just size. If we expand the ntfs boot sector, it would occupied 5 sectors, this would push the ext2 code backward. Although it's possible to handle this with some #ifdef's, but I'm not fond of conditional compilation. Also, it would break the linkage with grubinst as well.

No problem for 5 sectors or more.

Not difficult. Just use this directive:

```
#if (defined(GRLDR_MBR)) || (defined(GRLDR_INSTALL))
```

for a grldr.mbr, and this one:

```
#if (! defined(GRLDR_MBR)) && (! defined(GRLDR_INSTALL))
```

for grldr.

(Note that GRLDR_INSTALL is for a slightly modified grldr.mbr embedded in bootlace.com, while GRLDR_MBR is for the independent grldr.mbr file.)

So I think no need to strip out the ext2 code. Better keep it as it is.

grldr need not be touched, because it works fine for old Windows. All we have to handle is about GRLDR.MBR. And for GRLDR.MBR, we do not mind if it could exceed 8KB, in the case of grub4dos.

> **bean123 said:**
> 
There is a trick to solve this. We can use the $INDEX_ALLOCATION attribute to get a bitmap of currently used blocks. The ntfs driver in grub4dos and grub2 already have code to handle this situation.

Good! If we can do, why not?

---

### Post by ago on 2008-05-20
For your info I truncate grldr.mbr to 8k using dd.

---

### Post by tinybit on 2008-05-20
you can dd 8K of grldr to create your own grldr.mbr for use with boot.ini.

but the grldr.mbr along with the grub4dos release cannot be shorten to 8K. doing so will not work for you.

---

### Post by ago on 2008-05-20
> **tinybit said:**
> you can dd 8K of grldr to create your own grldr.mbr for use with boot.ini.
that is what I do (as suggested by bean123)

---

### Post by crate2k5 on 2010-02-20
As I looked up this thread error went away and loaded normally. It was rather odd. Also, I am not following your process on how to fix the issue.

---

### Post by fwaokda on 2010-03-18
I'm having this problem but after reading through this thread am unsure what to do.  When I boot I select Ubuntu and then I get the following (might differ a little because it comes up and goes away so quickly)

Try hd(0,0) NTFS5: No wubildr
Try hd(0,1) NTFS5: No wubildr
Try hd(0,2)

Then I am taken to a type of command prompt.  How can I fix this without starting over because I have some files that I need to at the least retrieve.

Thanks for any help! :)

---

### Post by fwaokda on 2010-03-18
So I finally found a fix... here it is for anyone interested.

Keep in mind you can find out what your kernel version is by pressing TAB when it comes time to input it.

You can get your windows partition by doing the following command before typing everything in...

ls -l

You'll then get your partitions in the form of hd(0,0) the first digit is corresponds to a letter and the second a number. Like so,

hd(0,1) = sda1
hd(1,2) = sdb2 ... etc.

If your unsure which you need to use just try one after the other until your can boot up again.

Now here are the steps... (note "sh:grub>" is not something you type)

sh:grub> linux /boot/vmlinuz-[kernel version w/o brackets] root=/dev/[Windows Partition w/o brackets] loop=/ubuntu/disks/root.disk ro

sh:grub> initrd /boot/initrd.img-[kernel version w/o brackets]

sh:grub> boot

If you successfully boot then you need to reinstall the grub-pc otherwise you'll continue to have to retype all of that. So...

Once in Ubuntu...

1. Go to System>Administration>Synaptic Package Manager
2. Type in Quick Search "grub-pc"
3. Look for the one with the ubuntu logo and green square and right-click and mark for reinstallation.

Reboot and you should be good to go!
Thanks to the site where I got this from: [http://www.omaregan.com/?p=583](http://www.omaregan.com/?p=583)
You might be able to find more information about this problem by going to that site.

---

### Post by ferraz75 on 2010-04-02
Hi all!
Firs of all thanks for all the info.

It seems that I don't have kernel. Is it possible? I've no 'vmlinuz-...' like file at boot/
What can I do?

Thnx!

---

### Post by emptystorage on 2011-07-28
Hi all,

I had the same problem as the original poster and [SOLVED] it in a very simple way. Here's my story:

I installed Ubuntu 11.04 64-bit using Wubi in Vista and a clean ISO. I got the "Try hd(0,0): NTFS5: No wubildr" error and after a minute or so, Grub loaded and Ubuntu booted. I wanted to find a fix for the wait.

I discovered that my first partition [ hd(0,0) ] is a small (FAT?) partition Windows uses to store it's MBR and a few other things. My second partition [ hd(0,1) ] is my C: drive where Windows lives and where Wubi put Ubuntu.

So, the Windows Boot Loader was looking for "wubildr" on my first partition when really it was on my second partition where Wubi put it.

To correct this, I copied wubildr to the 1st partition. I don't know how to access the 1st partition from Windows, but it can be mounted and accessed easily in a Linux command prompt.

Note: this solution was successful with Ubuntu installations on both the 2nd and 3rd partitions.

---

### Post by prishank799 on 2011-08-14
> **emptystorage said:**
> Hi all,

I had the same problem as the original poster and [SOLVED] it in a very simple way. Here's my story:

I installed Ubuntu 11.04 64-bit using Wubi in Vista and a clean ISO. I got the "Try hd(0,0): NTFS5: No wubildr" error and after a minute or so, Grub loaded and Ubuntu booted. I wanted to find a fix for the wait.

I discovered that my first partition [ hd(0,0) ] is a small (FAT?) partition Windows uses to store it's MBR and a few other things. My second partition [ hd(0,1) ] is my C: drive where Windows lives and where Wubi put Ubuntu.

So, the Windows Boot Loader was looking for "wubildr" on my first partition when really it was on my second partition where Wubi put it.

To correct this, I copied wubildr to the 1st partition. I don't know how to access the 1st partition from Windows, but it can be mounted and accessed easily in a Linux command prompt.

Note: this solution was successful with Ubuntu installations on both the 2nd and 3rd partitions.


Here's how I did it (in WIndows 7 though).
I went to control panel and searched the word "partition". A result "Create and format hard disk partition" under Administrative tools will show up.
Click on the "Create and format hard disk partition". The disk management dialogue box will open.
Look below.
You will see "System Reserved", (C:), (D:) and/or any other partition that you might have with their respective letters.
Right click on the "System Reserved", select "Change Drive letters and paths". In the new dialogue box, click "add" and then "OK" on the new dialogue box that appears. You should receive a notification similar to the one when you plug in a pendrive.
Now, go to the directory where you installed Ubuntu/Kubuntu, search for and copy the file wubildr and then paste it in the new partition that should have appeared in My Computer. (Do not do anything else to the new partition as it contains system files and might damage your Windows.)
After that, open disk management again and then remove the drive letter from "System Reserved". (You will get a warning about removing the drive letter bu do it, nothing will happen - at least nothing happened on my computer).
Then restart the computer. Ubuntu/Kubuntu should load normally without the "ntfs no wubildr" message.
P.S do it at your own risk, I am not responsible for any damage that might occur.

---

### Post by jeet on 2012-05-06
Thanks a lot prishank799. This solution fixed my problem.

---

### Post by oldos2er on 2012-05-06
Old thread closed.

---


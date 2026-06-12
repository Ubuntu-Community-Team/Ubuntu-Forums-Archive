---
title: "GRUB4DOS bug fix"
date: 2007-04-24
forum: General Help
---

### Post by fvb on 2007-04-24
Hello,

I wanted to write a message for my [Dutch blog]("http://monitor.volkskrantblog.nl/") on Wubi.
Downloading went fine, after reboot I got the boot menu.
But Ubuntu won't load:
FIND--SET-ROOT/WUBI/BOOT/MENU.LIST
ERROR 17 FILE NOT FOUND

Thanks,
Frans

---

### Post by Scortech on 2007-04-25
I got this message too.I am new to wubi and ubuntu so I just uninstalled ubuntu and wubi..

---

### Post by ago on 2007-04-25
Problens that cause error 17 generally are:

* initrd or linux kernel are fragmented 
* the filesystem is compressed
* the filesystem is on a raid array
* peculiar drivers are required to acces the hard disk

A solution is usually to install on a different partition (it is usually sufficient to cut and paste the wubi folder to a different drive). If fragmentation is the problem defragmenting does help.

---

### Post by Temujin_12 on 2007-04-27
Those are good suggestions.  I've been following Wubi for quite some time and run into error 17 on every version.  Here's what I've tried:

[LIST]
[*]Defragment hard drive using both default XP defregmentor and a more professional version (which I think was diskeeper)
[*]Do the menu.1st copy paste again thing
[*]Used contig ([http://www.microsoft.com/technet/sysinternals/utilities/contig.mspx](http://www.microsoft.com/technet/sysinternals/utilities/contig.mspx)) to manually defragment c:\wubi.
[/LIST]

None of which have worked yet.  I'm wondering if I fall under the "peculiar drivers are required to acces the hard disk" scenario.  I'm running it on a Compaq Presario 2100 on which live CDs (of different variants) work fine and I am able to mount my ntfs drive using them.

If anyone is able to get Wubi to work on a Presario 2100 let me know.  I'll try minefield today and post my findings.

---

### Post by celsus on 2007-05-04
I have the same problem as fvb.  I installed wubi to D: the original 20GB IDE HD that came with my eMachines T1220.  D: is not part of a RAID, it is not compressed; it isn't even fragmented, but it won't boot.  The loader can't find /WUBI/BOOT/MENU.LIST (I see there is one in boot and another in its subdirectory, wingrub), but just before it displays the error message it is apparently looking on A:

---

### Post by Lightspeed on 2007-05-05
> **ago said:**
> Problens that cause error 17 generally are:

* initrd or linux kernel are fragmented 
* the filesystem is compressed
* the filesystem is on a raid array
* peculiar drivers are required to acces the hard disk

A solution is usually to install on a different partition (it is usually sufficient to cut and paste the wubi folder to a different drive). If fragmentation is the problem defragmenting does help.

I had this problem suddenly appear in minefield3 and I'm sure that none of these are my problem.

* That contig program reports that neither file is fragmented
* It's just NTFS and nothing in the wubi folder is compressed
* Not on a RAID array
* Minefield2 got into Ubuntu fine so I doubt it's my hard drive's drivers.

Also like celsus, it is looking on A: (floppy drive) for some reason. There isn't a disk in there.

---

### Post by jasw on 2007-05-09
I'm also having a probelm with Error 17. The drive is not compressed and I've run contig to defrag c:\wubi so there's no problem there, but I did notice that it was looking in the A: like with Lightspeed and celcus, so I tried disabling the floppy in the BIOS and even removed it, but then it didn't look for the file it just said Error 17 straight away.

---

### Post by ago on 2007-05-09
> **jasw said:**
> I'm also having a probelm with Error 17. The drive is not compressed and I've run contig to defrag c:\wubi so there's no problem there, but I did notice that it was looking in the A: like with Lightspeed and celcus, so I tried disabling the floppy in the BIOS and even removed it, but then it didn't look for the file it just said Error 17 straight away.

Ok then try to use

find --set-root --ignore-floppies /wubi/grub/menu.lst

You may need to edit both c:\menu.lst and c:\wubi\grub\menu.lst

let me know if it works

---

### Post by jasw on 2007-05-09
ok I tried that but it does the same as what it did when I unplugged the floppy drive, it doesn't look for the file it just says Error 17 straight away.

---

### Post by ago on 2007-05-09
try replacing c:\grldr and c:\grub.exe with the files in [http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-09.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-09.zip)

---

### Post by jasw on 2007-05-09
I tried replacing those files, now I get a message saying that the number of cynlinders and number of sectors aren't equal to number defined in the BIOS, then followed by Error 17 again.

---

### Post by ago on 2007-05-09
Jasw, thanks for your help. I have contacted the devs of grldr, hopefully they will be able to help, my understanding of grldr is very limited. Ecology was also able to reproduce the error, so we'll keep looking for a solution, but I am out of ideas for the time being.

---

### Post by jasw on 2007-05-09
ok, thanks for your help as well.

---

### Post by fontenot_1031 on 2007-05-09
Same error here too.  Dang

---

### Post by overclock2099 on 2007-05-09
Same here. I'm using an up to date system.
It's looking for the bootloader, check the a drive and then throws the error 17.

I'm using a standard seagate sata drive and nvidia sata controller and have no problems booting to a livecd.

-oc

---

### Post by overclock2099 on 2007-05-09
> **Temujin_12 said:**
> Those are good suggestions.  I've been following Wubi for quite some time and run into error 17 on every version.  Here's what I've tried:

[LIST]
[*]Defragment hard drive using both default XP defregmentor and a more professional version (which I think was diskeeper)
[*]Do the menu.1st copy paste again thing
[*]Used contig ([http://www.microsoft.com/technet/sysinternals/utilities/contig.mspx](http://www.microsoft.com/technet/sysinternals/utilities/contig.mspx)) to manually defragment c:\wubi.
[/LIST]



Running contig fixed my problem but i had to use the -s switch to recusivly defrag the c:\wubi folder. 
ie. contig -v -s c:\wubi

Took about 5 minutes and it worked after that,

-oc

---

### Post by digeratiX on 2007-05-10
I tried the swap over of the new grub.exe and the gldr file and nothing, even MORE errors about bios crap.

Im washing my hands of this time wasting piece of crap.

---

### Post by allforcarrie on 2007-05-10
this is a great idea in concept, if it worked it would be outstanding. I hope one day they can get this built into Ubuntu.

---

### Post by tinybit on 2007-05-11
> FIND--SET-ROOT/WUBI/BOOT/MENU.LIST
> ERROR 17 FILE NOT FOUND

Oh, This might be a typo: MENU.LIST ----> menu.lst

Also upper case letters should be changed to lower case letters. 

And there should be spaces between command, options and filenames:

find        --set-root          /wubi/boot/menu.lst

---

### Post by ago on 2007-05-11
Hi tinybit, thanks a lot for helping out. I cannot reproduce the error on my machine and cannot test, but another of our devs used tab completion at the grub shell to explore the filesystem and confirmed that folders/files below /wubi/boot are not visible (that only happens on some peculiar situation, we do not yet know why). I can confirm though that in the menu.lst we ship the spelling is correct:

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst

---

### Post by bean123 on 2007-05-11
Fix a few bugs in the NTFS module.

Support NTFS compression (experimental).

---

### Post by ago on 2007-05-11
> **bean123 said:**
> Fix a few bugs in the NTFS module.

Support NTFS compression (experimental).

Bean that is going to help A LOT. Thank you very much! We'll test it in next build (tonight or this w/e). Do you think I still need to reduce the depth of the path or can I keep the files in c:\wubi\boot\grub\? Can it handle fragmented kernel/initrd (that would also be very useful since it is difficult to defragment on our side).

---

### Post by ago on 2007-05-11
To all users that had problems with grldr error 17 please try to download the zip file above, unzip glrdr into c:\, try again and let us know how it goes.

---

### Post by bean123 on 2007-05-11
> **ago said:**
> Bean that is going to help A LOT. Thank you very much! We'll test it in next build (tonight or this w/e). Do you think I still need to reduce the depth of the path or can I keep the files in c:\wubi\boot\grub\? Can it handle fragmented kernel/initrd (that would also be very useful since it is difficult to defragment on our side).

it should be able to handle fragmented files.

---

### Post by ago on 2007-05-11
Can I send you a beer or a pizza?

---

### Post by tinybit on 2007-05-11
> **ago said:**
> Do you think I still need to reduce the depth of the path or can I keep the files in c:\wubi\boot\grub\?

Now I think you needn't reduce the depth of the path. And I think Bean will solve all those problems. Just feel free to report bugs.

---

### Post by ago on 2007-05-11
> **tinybit said:**
> Now I think you needn't reduce the depth of the path. And I think Bean will solve all those problems. Just feel free to report bugs.

Thanks a lot again, you guys have been very responsive and efficient!

---

### Post by ago on 2007-05-11
Minefield 0.7 includes the grub bug fix [http://ubuntuforums.org/showthread.php?t=440609](http://ubuntuforums.org/showthread.php?t=440609)

---

### Post by ddunham on 2007-05-13
Is there anything else I can try to get around the Error 17?  I've tried 7.04-test2 and I tried one a few days ago that was something else (don't have it recorded and it's since been destroyed).  In all cases, I get a File not found on the 'find'.

I pulled down the new grldr for the old installation and that didn't seem to do anything.  Contig says that all files in my C:\wubi are continguous except for system.virtual.disk. and I've confirmed that I'm not doing any compression on the drive.

Anything else that I should be trying?  

Thanks!

-- 
Darren

---

### Post by ago on 2007-05-13
> **ddunham said:**
> Is there anything else I can try to get around the Error 17?  I've tried 7.04-test2 and I tried one a few days ago that was something else (don't have it recorded and it's since been destroyed).  In all cases, I get a File not found on the 'find'.

I pulled down the new grldr for the old installation and that didn't seem to do anything.  Contig says that all files in my C:\wubi are continguous except for system.virtual.disk. and I've confirmed that I'm not doing any compression on the drive.

Anything else that I should be trying?  

Thanks!

-- 
Darren

I'll forward to grub4dos devs, in the meantime you can try to move the files up one level, but that is slightly more involved ([http://ubuntuforums.org/showpost.php?p=2631000&postcount=27](http://ubuntuforums.org/showpost.php?p=2631000&postcount=27) ). Anybody else having problems with error 17 with wubi-test2?

---

### Post by ddunham on 2007-05-13
Yes, moving everything up to C:\ worked.  I tried just moving them up to C:\wubi and that didn't seem to have any effect.  

Is there any information from this installation that would be useful for tracking down the issue?

Thanks again.
-- 
Darren

---

### Post by bean123 on 2007-05-13
Well, it seems there is still problem in fsys_ntfs.c. The code is a little mess up, and it's not easy to detect bugs. I plan to rewrite the code, please be patient.

---

### Post by jonash on 2007-05-14
->Anyone else go the problem?
Yes I have the same problem with error 17. 

I have also used defrag (win and GNU), contig, and uncomressed my drive. 

I'll try moving the files to c:\ today

---

### Post by ago on 2007-05-14
> **bean123 said:**
> Well, it seems there is still problem in fsys_ntfs.c. The code is a little mess up, and it's not easy to detect bugs. I plan to rewrite the code, please be patient.

Thanks bean, much appreciated!

---

### Post by jasw on 2007-05-15
After trying the latest build (test2), I still can't get it to work and face Error 17. However, I decided to try to install it on my old PC, which uses an IDE HDD instead of a SATA one, and...success! So it seems there may be a problem with it trying to detect SATA drives, as the floppy drive is an IDE drive and it only wants to look in there. Hopefully you can get this fixed in the next build.

---

### Post by tinybit on 2007-05-15
> **jasw said:**
> After trying the latest build (test2), I still can't get it to work and face Error 17. However, I decided to try to install it on my old PC, which uses an IDE HDD instead of a SATA one, and...success! So it seems there may be a problem with it trying to detect SATA drives, as the floppy drive is an IDE drive and it only wants to look in there. Hopefully you can get this fixed in the next build.

GRLDR uses BIOS to access files on the disk. So the problem should not be related to SATA/SCSI/IDE. It is a "soft" problem. Our developer Bean is currently working hard on it.

---

### Post by bean123 on 2007-05-16
I have rewritten fsys_ntfs.c, please test the new version.

fstest.exe is a console mode program which can be used to test the new NTFS code in Windows environment. 

Usage:

fstest.exe [-l] [-x] [-c] filename [base] [leng]

-l
List files.

-x
Hex dump.

-c
Compare mode. It first read the file using NTFS code, then Windows API, and compare the results.

filename
Must use absolute path.

base
Optional. It is used to specify the offset (in sectors) for -x or -c.

leng
Optional. It is used to specify the length (in sectors) for -x or -c.

---

### Post by ago on 2007-05-16
Thanks bean, I will be able to do a new release only tonight. Bean ,we are also using grldr.mbr these days with vista (following your guide), would it be possible to get that too? Also does the above take care of compressed/fragmented files?

For the others, can you please uncompress the above file into c:\ and see if that solves error 17? Thanks a lot. Please report back any success/unsuccess.

---

### Post by bean123 on 2007-05-16
Here is it.

BTW, you can get grldr.mbr from the grub utilities project:

[http://download.gna.org/grubutil/](http://download.gna.org/grubutil/)

To extract the embeded grldr.mbr:

grubinst -o c:\grldr.mbr

grldr.mbr use assembly to access NTFS, it's different from the file system driver in grub.

---

### Post by linlay on 2007-05-16
> **jasw said:**
> After trying the latest build (test2), I still can't get it to work and face Error 17. However, I decided to try to install it on my old PC, which uses an IDE HDD instead of a SATA one, and...success! So it seems there may be a problem with it trying to detect SATA drives, as the floppy drive is an IDE drive and it only wants to look in there. Hopefully you can get this fixed in the next build.

i'm also STILL having the error17 problem. I'm on a HP laptop with a SATA hdd ...
and i'm using the latest wubi test(2)

---

### Post by ago on 2007-05-16
Can you please:

1)  download [http://ubuntuforums.org/attachment.php?attachmentid=32728&d=1179305464](http://ubuntuforums.org/attachment.php?attachmentid=32728&d=1179305464)
2) Extract grldr into C:\ (overwriting existing file)
3) Reboot.
4) Give as feedback

Thx

---

### Post by bean123 on 2007-05-16
I just fix a new bug in the NTFS code, please use the update version for testing.

---

### Post by ecology2007 on 2007-05-16
Thanks bean, i will integrate this in a few minutes.

---

### Post by ecology2007 on 2007-05-16
I ran fstest on a few files from a dos cmd box inside windows.
```
fstest.exe "d:\wubi\boot\winboot"
```File Size 0
Base too large
```
fstest.exe "d:\wubi\boot\winboot\"
```NTFS DIR 17```
fstest.exe -l "d:\wubi\boot\winboot\"
```NTFS DIR 17
```
fstest.exe -c "d:\wubi\boot\winboot\"
```NTFS DIR 17
```
fstest.exe -c "d:\wubi\boot\winboot\menu.lst"
```File Size 1867
Comparing
Succeed

So far so good, provided it did not handle that drive very well, and could not reach or see the content of wubi folder using grub command line.
What does base too large means ? I think it occurs when i target folders and not terminate the path with a "\".

---

### Post by bean123 on 2007-05-16
"Base too large" means base <= file length, it will happen if file size is zero.

---

### Post by ecology2007 on 2007-05-16
I have just updated wubi with the latest files you provided.

grldr does not start anymore.
grldr is on c:, with its menu.lst.

I get a message like this one :

(hd0,0) : NTFS
(hd0,1) : NTFS

grldr has not been found on any drive.
Please press ctrl alt del.

Do I need to put grldr.mbr here too or is it only for vista bcedit ?

---

### Post by jasw on 2007-05-16
Right, I've replaced gldr with the new one from bean's thread (the link you provide in the above pst appears to be dead) and it's a partial success. This is what happens:

Install Wubi in Windows
Replace gldr
Restart
Select Ubuntu, NO ERROR 17, it detects the files and installs Ubuntu
Installation goes fine, finishes, then tells me it needs to reboot and does so automatically
Select Ubuntu and get ERROR 17.

So, we're getting there, just a few tweaks and it should be good. Thanks for all the help and hard work, I greatly appreciate it and here's hoping it can be fixed becuase I've been using this on another PC and it's absolutely brilliant.

EDIT: I've also noticed a new message before I get Error 17, which says: No $INDEX_ROOT

---

### Post by ecology2007 on 2007-05-16
I got it starting by copying grldr and menu.lst to both c: and d:.
That sounds weird to me, but it works.

The first menu lst we are using is this one :
> title Ubuntu
find --set-root --ignore-floppies /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst/wubi/boot/grub/menu.lst is on d:
> title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=kubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot
i assume it searches for a grldr when it finds the configfile and that's why it starts when i put grldr on d:, but is it expected behavior ?

Keep on good work, we have less and less error 17.

---

### Post by ago on 2007-05-16
With the new grldr I have:

> 
find --set-root ....
No $INDEX_ROOT

Error 17: File not found


browsing the file system in grub shell, I can see /wubi/ content, but if I try autocompletion from /wubi/bo[TAB] I get No $INDEX_ROOT

old grldr works fine. The above only happens on second reboot (after installing, which I alters /wubi/boot)

fstest.exe "c:\wubi\boot\linux"
No $INDEX_ROOT
ntfs_dir: 18

---

### Post by bean123 on 2007-05-16
Please download nfi.exe from ms:

[http://support.microsoft.com/kb/253066](http://support.microsoft.com/kb/253066)

Then try the following commands:

nfi c:\wubi
nfi c:\wubi\boot
nfi c:\wubi\boot\linux

---

### Post by tinybit on 2007-05-16
> **ecology2007 said:**
> I have just updated wubi with the latest files you provided.

grldr does not start anymore.
grldr is on c:, with its menu.lst.

I get a message like this one :

(hd0,0) : NTFS
(hd0,1) : NTFS

grldr has not been found on any drive.
Please press ctrl alt del.

Do I need to put grldr.mbr here too or is it only for vista bcedit ?

I want to ask Bean why? Also updated NTFS bootsector code?

---

### Post by ago on 2007-05-17
> **bean123 said:**
> Please download nfi.exe from ms:

Bean, I can only try that tonight, I will let you know.

---

### Post by bean123 on 2007-05-17
Update: fix more bugs, and improve fstest.exe.

Usage:
  fstest info pathname
  fstest list pathname
  fstest comp filename [offset] [length]
  fstest [-b] dump filename [offset] [length]
  fstest [-b] inode filename

Commands:

info
display basic info

list
List mode.

comp
Compare mode. It first read the file using NTFS code, then Windows API, and compare the results.

dump
Dump mode.

inode
Display the MFT associated with filename

Parameters:

-b
Binary mode. It's use to ouput raw data to standard output. For example,

fstest -b inode C:\filename > aa

Then you can analyse the output with a hex editor.

filename
In the new version, you can use a MFT number instead of real name. For example, C:\#0x1B means the file whose MFT number is 0x1B.

offset
Optional. It is used to specify the offset (in bytes) for comp and dump.

leng
Optional. It is used to specify the length (in bytes) for comp and dump.

---

### Post by ecology2007 on 2007-05-17
Ok i found the nfi.exe in 
[http://download.microsoft.com/download/win2000srv/utility/3.0/nt45/en-us/oem3sr2.zip](http://download.microsoft.com/download/win2000srv/utility/3.0/nt45/en-us/oem3sr2.zip)
I did put it in my windows folder.
I think you asked it for ago but i still give you my results.

```

D:\>nfi d:\wubi
NTFS File Sector Information Utility.
Copyright (C) Microsoft Corporation 1999. All rights reserved.

\wubi
    $STANDARD_INFORMATION (resident)
    $FILE_NAME (resident)
    $INDEX_ROOT $I30 (resident)
    $INDEX_ALLOCATION $I30 (nonresident)
        logical sectors 21473680-21473687 (0x147a990-0x147a997)
    $BITMAP $I30 (resident)

```
```
D:\>nfi d:\wubi\boot
NTFS File Sector Information Utility.
Copyright (C) Microsoft Corporation 1999. All rights reserved.

\wubi\boot
    $STANDARD_INFORMATION (resident)
    $FILE_NAME (resident)
    $INDEX_ROOT $I30 (resident)

``````
D:\>nfi d:\wubi\boot\linux
NTFS File Sector Information Utility.
Copyright (C) Microsoft Corporation 1999. All rights reserved.

\wubi\boot\linux
    $STANDARD_INFORMATION (resident)
    $FILE_NAME (resident)
    $DATA (nonresident)
        logical sectors 52721120-52724535 (0x32475e0-0x3248337)

```

---

### Post by ago on 2007-05-17
Still same issue with new grldr: No $INDEX_ROOT on boot
Now when I try to autocomplete from command line I get: 

```

configfile (hd0,1)/wubi/b[tab]Non-resident attribute list not supported
No $INDEX_ROOT
boot

configfile (hd0,1)/wubi/boot/[tab]Non-resident attribute list not supported
No $INDEX_ROOT

Error 18: Inconsistent filesystem structure

```

```

C:\>fstest.exe info "c:\wubi"
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8

C:\>fstest.exe info "c:\wubi\boot"
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8

C:\>fstest.exe info "c:\wubi\boot\grub"
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8

C:\>fstest.exe list "c:\wubi\"
ntfs_dir: 17

C:\>fstest.exe list "c:\wubi\boot\"
ntfs_dir: 17

C:\>fstest.exe list "c:\wubi\boot\grub"
Non-resident attribute list not supported
No $INDEX_ROOT
ntfs_dir: 18

C:\>fstest.exe list "c:\wubi\"
ntfs_dir: 17

C:\>fstest.exe comp "c:\wubi\boot"
ntfs_dir: 17

C:\>fstest.exe comp "c:\wubi\boot\grub"
Non-resident attribute list not supported
No $INDEX_ROOT
ntfs_dir: 17

```

```


C:\>nfi c:\wubi
NTFS File Sector Information Utility.
Copyright (C) Microsoft Corporation 1999. All rights reserved.

\wubi
    $STANDARD_INFORMATION (resident)
    $FILE_NAME (resident)
    $INDEX_ROOT $I30 (resident)
    $INDEX_ALLOCATION $I30 (nonresident)
        logical sectors 16970080-16970087 (0x102f160-0x102f167)
    $BITMAP $I30 (resident)

C:\>nfi c:\wubi\boot
NTFS File Sector Information Utility.
Copyright (C) Microsoft Corporation 1999. All rights reserved.

\wubi\boot
    $STANDARD_INFORMATION (resident)
    $ATTRIBUTE_LIST (nonresident)
        logical sectors 16987008-16987015 (0x1033380-0x1033387)
    $INDEX_ALLOCATION $I30 (nonresident)
        logical sectors 17035272-17035279 (0x103f008-0x103f00f)
    $BITMAP $I30 (resident)

C:\>nfi c:\wubi\boot\grub
NTFS File Sector Information Utility.
Copyright (C) Microsoft Corporation 1999. All rights reserved.

\wubi\boot\grub
    $STANDARD_INFORMATION (resident)
    $FILE_NAME (resident)
    $INDEX_ROOT $I30 (resident)


```

---

### Post by bean123 on 2007-05-17
Oh, you have non-resident $ATTRIBUTE_LIST in \wubi\boot !

 i ignore non-resident attribute list because i thought it's very rare, but i have to reconsider this assumption now.

---

### Post by linlay on 2007-05-17
i've used the files given in this thread:
[http://ubuntuforums.org/showthread.php?t=439965&page=2](http://ubuntuforums.org/showthread.php?t=439965&page=2)

and now it works FINE! YEAH!

Please include those in the official release of wubi. thanks.

---

### Post by linlay on 2007-05-18
i've celebrated too early!
I;m still having the same prob as jasw.

I managed to boot onto ubuntu the first time, and installation started. Once i was asked to restart the computer, and when i go back to the ubunto selection i get ERROR17 again!
(And on top of that error there is: No $INDEX_ROOT)

If anyone could help? :)

---

### Post by ago on 2007-05-18
Bean123 is working on it. A patch will probably be out soon. Be patient.

---

### Post by linlay on 2007-05-19
any idea around when this fix will be available ?

Thanks alot ...really waiting to try out ubuntu :p

---

### Post by ecology2007 on 2007-05-19
Nope, give him some time, he is rewriting the ntfs driver for grub, and MS does not give documentation for its filesystem.

---

### Post by ecology2007 on 2007-05-19
Nope, give him some time, bean123 is rewriting the ntfs driver for grub, and MS does not give documentation for its filesystem.

---

### Post by Nokonium on 2007-05-19
I get 'Error 17: Can't find file' as well, I have no compression, did a defrag maximising free space, no RAID ....

I have opened menu.1st and find 

```
title Ubuntu (Original Kernel)
find --set-root /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot
```

ubuntu-7.04-alternate-i386.iso is in wubi/install, in wubi/boot there is a linux file, a initrd file and two folders Grub and Winboot.

Do you think that ```
/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso 
```

Needs ubuntu-7.04-alternate-i386.iso in the boot folder?

---

### Post by ago on 2007-05-20
> **Nokonium said:**
> 
Needs ubuntu-7.04-alternate-i386.iso in the boot folder?

Nope the ISO is under /wubi/install

---

### Post by mikaelhc on 2007-05-20
I had the same problem: EFI showed a non-resident $ATTRIBUTE_LIST on "\wubi\boot" and I got the "No $INDEX_ROOT" error when booting WUBI.

A quick workaround (for me at least) was to copy the "\wubi\boot" directory to another location on the same disc, delete the original files, and copy the files back. After this Ubuntu booted fine.

---

### Post by jasw on 2007-05-20
That method works for me too. Now I'm enjoying Ubuntu in all it's goodness :D. Thanks to everyone here who's helped, your work is very much appreciated.

---

### Post by tuxcantfly on 2007-05-20
stickying thread, seems like a lot of users are having this issue...

---

### Post by syllepsa on 2007-05-21
I also had problem with "error 17 file not found..." but after replacing grdlr file in main directory and in c:\wubi\boot\winboot\  I was able to install Ubuntu ;)

After booting system "No $INDEX_ROOT" problem appeared. So I did workaround  described by mikaelhc and now I enjoy my new Ubuntu.


Thanks for your work!!

Mariusz   

P.S. By no means WUBI will make that new users migrate to Ubuntu.

---

### Post by linlay on 2007-05-21
I just tried the fix ...and IT WORKS

YEAH THANK YOU!
(And i'm posting this from Firefox running on ubuntu hehe)

---

### Post by bean123 on 2007-05-22
Please try the new version, see if it fix the "No $INDEX_ROOT" problem.

---

### Post by ago on 2007-05-22
Thanks a lot bean!!  I will be able to test it tonight and let you know. We will push a new minefield soon. If preliminary tests are satisfactory that will make it into our main download.

For the others: if you experienced error 17 and/or "No $INDEX_ROOT" issues, please try the new grldr above (no other workaround should be needed).

---

### Post by bean123 on 2007-05-22
Oh, i found yet another bug, it happens when the MFT table itself uses attribute list.

---

### Post by Computer Guru on 2007-05-22
Bean, is there any way to modify grldr to run a command?

For instance, take a section from menu.lst and embed it into a copy of GRLDR, so that I can chainload to GRLDR (from NTLDR or BCD) and bypass the menu.lst file completely?

---

### Post by ago on 2007-05-22
> **bean123 said:**
> Oh, i found yet another bug, it happens when the MFT table itself uses attribute list.

Now it freezes after the find --set-root command. If I do tab expansion after (hd0,1)/wubi/bo[tab] it also freezes. No error messages.

```


C:\>fstest.exe info "c:\wubi"
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

C:\>fstest.exe info "c:\wubi\boot"
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

C:\>fstest.exe info "c:\wubi\boot\grub"
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

C:\>fstest.exe info "c:\wubi\boot\linux"
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

C:\>fstest.exe list "c:\wubi"
00005307             0  [wubi]

C:\>fstest.exe list "c:\wubi\boot"
0000530D             0  [boot]

C:\>fstest.exe list "c:\wubi\boot\grub"

```

Last command jams the shell

---

### Post by ecology2007 on 2007-05-22
To Computer Guru : 
What are the possibilities for us to use EasyBCD ?
Could you work with us to plant its mechanisms in Wubi ?
Does it have a dll or a commandline we could use ?

---

### Post by bean123 on 2007-05-22
Try this command:

fstest inode C:\wubi

fstest inode C:\wubi\boot

---

### Post by ago on 2007-05-22
C:\>fstest.exe inode "c:\wubi"
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    wubi
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    5722248+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)

C:\>fstest.exe inode "c:\wubi\boot"
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $ATTRIBUTE_LIST (0x20) (nr,sz=184)
    7063416+8
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    10372960+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
Can't find 0x0 in attribute list

C:\>fstest.exe inode "c:\wubi\boot\grub"
[jammed here]

---

### Post by bean123 on 2007-05-22
> **Computer Guru said:**
> Bean, is there any way to modify grldr to run a command?

For instance, take a section from menu.lst and embed it into a copy of GRLDR, so that I can chainload to GRLDR (from NTLDR or BCD) and bypass the menu.lst file completely?

Yes, you can modify the preset menu with grubmenu:

grubmenu export grldr psmenu.lst

modify psmenu.lst, then

grubmenu import grldr psmenu.lst

The original preset menu is used to find menu.lst, you can change it to whatever you want.

You may also want to rename or remove the menu.lst in the same directory as grldr, otherwise it will take preference over the embeded preset menu.

grubmenu is part of "GRUB Utilities" project, you can get it at the following url:

[http://download.gna.org/grubutil/](http://download.gna.org/grubutil/)

---

### Post by bean123 on 2007-05-22
It seems the handling of attribute list is still faulty, please dump the on disk structure with:

fstest dump C:7063416+8
fstest dump C:10372960+8

Also, use:

fstest -v inode C:\wubi\boot

to dump the MFT of C:\wubi\boot

The output is huge, you may want to capture it in a file.

---

### Post by Computer Guru on 2007-05-23
Thanks Bean, that's *very* helpful!

Currently I'm using Stage1 + Stage2 with some modifications to the code in order to get it to boot with the Vista bootmenu (I was inserting the location of Stage2 into sTage1, then using BCD to chainload Stage1 which in turns finds and opens stage2, but **so many problems!**. I'm rewriting it to use this new GRLDR instead (and linking to the Grub4Dos project from the app too :))

I'm trying to get Windows XP to boot *without* going through a second boot menu (i.e. without NTLDR at all), so a separate GRLDR with an embedded menu.lst is just genius :)

Bean, one more thing:
Is it possible to recover the *Ubuntu* GRUB bootloader with grub.exe?
Like on an Ubuntu partition, let's say I have /boot/grub/menu.lst and GRUB installed to the MBR.
I install Windows, and overwrite the MBR; I now want to install GRUB to the *bootsector* of the Ubuntu partition. Is it possible to do so from *within Windows* using GRUB.exe instead of having to boot with a live CD and use ```
grub
setup (hdx,y)
exit
``` instead?

**ecology**: We had a post a while back about creating an EasyBCD API, but unfortunately there was little interest (actually none at all) at the time.

However, we're all about making things easier, and the code is already there. Please do shoot me an email, and let's see where this goes. (ComputerGuru@NeoSmart.net) (Don't worry, the spammers already have it :))

---

### Post by ago on 2007-05-23
```


C:\>fstest dump C:7063416+8
00000000: 10 00 00 00  20 00 00 1A  00 00 00 00  00 00 00 00 ; .... ...........
00000010: 15 53 00 00  00 00 1D 00  00 00 00 00  00 00 00 00 ; .S..............
00000020: 30 00 00 00  20 00 00 1A  00 00 00 00  00 00 00 00 ; 0... ...........
00000030: 24 53 00 00  00 00 19 00  00 00 00 00  00 00 00 00 ; $S..............
00000040: 90 00 00 00  28 00 04 1A  00 00 00 00  00 00 00 00 ; ....(...........
00000050: 3D 53 00 00  00 00 0B 00  00 00 24 00  49 00 33 00 ; =S........$.I.3.
00000060: 30 00 00 00  00 00 00 00  A0 00 00 00  28 00 04 1A ; 0...........(...
00000070: 00 00 00 00  00 00 00 00  15 53 00 00  00 00 1D 00 ; .........S......
00000080: 05 00 24 00  49 00 33 00  30 00 00 00  00 00 00 00 ; ..$.I.3.0.......
00000090: B0 00 00 00  28 00 04 1A  00 00 00 00  00 00 00 00 ; ....(...........
000000A0: 15 53 00 00  00 00 1D 00  04 00 24 00  49 00 33 00 ; .S........$.I.3.
000000B0: 30 00 00 00  00 00 00 00  4C 49 45 4E  54 5F 56 45 ; 0.......LIENT_VE
000000C0: 52 54 45 58  5F 41 52 52  41 59 5F 42  49 54 00 47 ; RTEX_ARRAY_BIT.G
000000D0: 4C 5F 43 4C  49 50 5F 50  4C 41 4E 45  30 00 47 4C ; L_CLIP_PLANE0.GL
000000E0: 5F 43 4C 49  50 5F 50 4C  41 4E 45 31  00 47 4C 5F ; _CLIP_PLANE1.GL_
000000F0: 43 4C 49 50  5F 50 4C 41  4E 45 32 00  47 4C 5F 43 ; CLIP_PLANE2.GL_C
00000100: 4C 49 50 5F  50 4C 41 4E  45 33 00 47  4C 5F 43 4C ; LIP_PLANE3.GL_CL
00000110: 49 50 5F 50  4C 41 4E 45  34 00 47 4C  5F 43 4C 49 ; IP_PLANE4.GL_CLI
00000120: 50 5F 50 4C  41 4E 45 35  00 47 4C 5F  43 4C 49 50 ; P_PLANE5.GL_CLIP
00000130: 5F 56 4F 4C  55 4D 45 5F  43 4C 49 50  50 49 4E 47 ; _VOLUME_CLIPPING
00000140: 5F 48 49 4E  54 5F 45 58  54 00 47 4C  5F 43 4F 45 ; _HINT_EXT.GL_COE
00000150: 46 46 00 47  4C 5F 43 4F  4C 4F 52 00  47 4C 5F 43 ; FF.GL_COLOR.GL_C
00000160: 4F 4C 4F 52  5F 41 52 52  41 59 00 47  4C 5F 43 4F ; OLOR_ARRAY.GL_CO
00000170: 4C 4F 52 5F  41 52 52 41  59 5F 42 55  46 46 45 52 ; LOR_ARRAY_BUFFER
00000180: 5F 42 49 4E  44 49 4E 47  00 47 4C 5F  43 4F 4C 4F ; _BINDING.GL_COLO
00000190: 52 5F 41 52  52 41 59 5F  42 55 46 46  45 52 5F 42 ; R_ARRAY_BUFFER_B
000001A0: 49 4E 44 49  4E 47 5F 41  52 42 00 47  4C 5F 43 4F ; INDING_ARB.GL_CO
000001B0: 4C 4F 52 5F  41 52 52 41  59 5F 50 4F  49 4E 54 45 ; LOR_ARRAY_POINTE
000001C0: 52 00 47 4C  5F 43 4F 4C  4F 52 5F 41  52 52 41 59 ; R.GL_COLOR_ARRAY
000001D0: 5F 53 49 5A  45 00 47 4C  5F 43 4F 4C  4F 52 5F 41 ; _SIZE.GL_COLOR_A
000001E0: 52 52 41 59  5F 53 54 52  49 44 45 00  47 4C 5F 43 ; RRAY_STRIDE.GL_C
000001F0: 4F 4C 4F 52  5F 41 52 52  41 59 5F 54  59 50 45 00 ; OLOR_ARRAY_TYPE.
00000200: 47 4C 5F 43  4F 4C 4F 52  5F 41 54 54  41 43 48 4D ; GL_COLOR_ATTACHM
00000210: 45 4E 54 30  5F 45 58 54  00 47 4C 5F  43 4F 4C 4F ; ENT0_EXT.GL_COLO
00000220: 52 5F 41 54  54 41 43 48  4D 45 4E 54  31 30 5F 45 ; R_ATTACHMENT10_E
00000230: 58 54 00 47  4C 5F 43 4F  4C 4F 52 5F  41 54 54 41 ; XT.GL_COLOR_ATTA
00000240: 43 48 4D 45  4E 54 31 31  5F 45 58 54  00 47 4C 5F ; CHMENT11_EXT.GL_
00000250: 43 4F 4C 4F  52 5F 41 54  54 41 43 48  4D 45 4E 54 ; COLOR_ATTACHMENT
00000260: 31 32 5F 45  58 54 00 47  4C 5F 43 4F  4C 4F 52 5F ; 12_EXT.GL_COLOR_
00000270: 41 54 54 41  43 48 4D 45  4E 54 31 33  5F 45 58 54 ; ATTACHMENT13_EXT
00000280: 00 47 4C 5F  43 4F 4C 4F  52 5F 41 54  54 41 43 48 ; .GL_COLOR_ATTACH
00000290: 4D 45 4E 54  31 34 5F 45  58 54 00 47  4C 5F 43 4F ; MENT14_EXT.GL_CO
000002A0: 4C 4F 52 5F  41 54 54 41  43 48 4D 45  4E 54 31 35 ; LOR_ATTACHMENT15
000002B0: 5F 45 58 54  00 47 4C 5F  43 4F 4C 4F  52 5F 41 54 ; _EXT.GL_COLOR_AT
000002C0: 54 41 43 48  4D 45 4E 54  31 5F 45 58  54 00 47 4C ; TACHMENT1_EXT.GL
000002D0: 5F 43 4F 4C  4F 52 5F 41  54 54 41 43  48 4D 45 4E ; _COLOR_ATTACHMEN
000002E0: 54 32 5F 45  58 54 00 47  4C 5F 43 4F  4C 4F 52 5F ; T2_EXT.GL_COLOR_
000002F0: 41 54 54 41  43 48 4D 45  4E 54 33 5F  45 58 54 00 ; ATTACHMENT3_EXT.
00000300: 47 4C 5F 43  4F 4C 4F 52  5F 41 54 54  41 43 48 4D ; GL_COLOR_ATTACHM
00000310: 45 4E 54 34  5F 45 58 54  00 47 4C 5F  43 4F 4C 4F ; ENT4_EXT.GL_COLO
00000320: 52 5F 41 54  54 41 43 48  4D 45 4E 54  35 5F 45 58 ; R_ATTACHMENT5_EX
00000330: 54 00 47 4C  5F 43 4F 4C  4F 52 5F 41  54 54 41 43 ; T.GL_COLOR_ATTAC
00000340: 48 4D 45 4E  54 36 5F 45  58 54 00 47  4C 5F 43 4F ; HMENT6_EXT.GL_CO
00000350: 4C 4F 52 5F  41 54 54 41  43 48 4D 45  4E 54 37 5F ; LOR_ATTACHMENT7_
00000360: 45 58 54 00  47 4C 5F 43  4F 4C 4F 52  5F 41 54 54 ; EXT.GL_COLOR_ATT
00000370: 41 43 48 4D  45 4E 54 38  5F 45 58 54  00 47 4C 5F ; ACHMENT8_EXT.GL_
00000380: 43 4F 4C 4F  52 5F 41 54  54 41 43 48  4D 45 4E 54 ; COLOR_ATTACHMENT
00000390: 39 5F 45 58  54 00 47 4C  5F 43 4F 4C  4F 52 5F 42 ; 9_EXT.GL_COLOR_B
000003A0: 55 46 46 45  52 5F 42 49  54 00 47 4C  5F 43 4F 4C ; UFFER_BIT.GL_COL
000003B0: 4F 52 5F 43  4C 45 41 52  5F 56 41 4C  55 45 00 47 ; OR_CLEAR_VALUE.G
000003C0: 4C 5F 43 4F  4C 4F 52 5F  49 4E 44 45  58 00 47 4C ; L_COLOR_INDEX.GL
000003D0: 5F 43 4F 4C  4F 52 5F 49  4E 44 45 58  45 53 00 47 ; _COLOR_INDEXES.G
000003E0: 4C 5F 43 4F  4C 4F 52 5F  4C 4F 47 49  43 5F 4F 50 ; L_COLOR_LOGIC_OP
000003F0: 00 47 4C 5F  43 4F 4C 4F  52 5F 4D 41  54 45 52 49 ; .GL_COLOR_MATERI
00000400: 41 4C 00 47  4C 5F 43 4F  4C 4F 52 5F  4D 41 54 45 ; AL.GL_COLOR_MATE
00000410: 52 49 41 4C  5F 46 41 43  45 00 47 4C  5F 43 4F 4C ; RIAL_FACE.GL_COL
00000420: 4F 52 5F 4D  41 54 45 52  49 41 4C 5F  50 41 52 41 ; OR_MATERIAL_PARA
00000430: 4D 45 54 45  52 00 47 4C  5F 43 4F 4C  4F 52 5F 4D ; METER.GL_COLOR_M
00000440: 41 54 52 49  58 00 47 4C  5F 43 4F 4C  4F 52 5F 4D ; ATRIX.GL_COLOR_M
00000450: 41 54 52 49  58 5F 53 47  49 00 47 4C  5F 43 4F 4C ; ATRIX_SGI.GL_COL
00000460: 4F 52 5F 4D  41 54 52 49  58 5F 53 54  41 43 4B 5F ; OR_MATRIX_STACK_
00000470: 44 45 50 54  48 00 47 4C  5F 43 4F 4C  4F 52 5F 4D ; DEPTH.GL_COLOR_M
00000480: 41 54 52 49  58 5F 53 54  41 43 4B 5F  44 45 50 54 ; ATRIX_STACK_DEPT
00000490: 48 5F 53 47  49 00 47 4C  5F 43 4F 4C  4F 52 5F 53 ; H_SGI.GL_COLOR_S
000004A0: 55 4D 00 47  4C 5F 43 4F  4C 4F 52 5F  53 55 4D 5F ; UM.GL_COLOR_SUM_
000004B0: 41 52 42 00  47 4C 5F 43  4F 4C 4F 52  5F 54 41 42 ; ARB.GL_COLOR_TAB
000004C0: 4C 45 00 47  4C 5F 43 4F  4C 4F 52 5F  54 41 42 4C ; LE.GL_COLOR_TABL
000004D0: 45 5F 41 4C  50 48 41 5F  53 49 5A 45  00 47 4C 5F ; E_ALPHA_SIZE.GL_
000004E0: 43 4F 4C 4F  52 5F 54 41  42 4C 45 5F  41 4C 50 48 ; COLOR_TABLE_ALPH
000004F0: 41 5F 53 49  5A 45 5F 45  58 54 00 47  4C 5F 43 4F ; A_SIZE_EXT.GL_CO
00000500: 4C 4F 52 5F  54 41 42 4C  45 5F 41 4C  50 48 41 5F ; LOR_TABLE_ALPHA_
00000510: 53 49 5A 45  5F 53 47 49  00 47 4C 5F  43 4F 4C 4F ; SIZE_SGI.GL_COLO
00000520: 52 5F 54 41  42 4C 45 5F  42 49 41 53  00 47 4C 5F ; R_TABLE_BIAS.GL_
00000530: 43 4F 4C 4F  52 5F 54 41  42 4C 45 5F  42 49 41 53 ; COLOR_TABLE_BIAS
00000540: 5F 53 47 49  00 47 4C 5F  43 4F 4C 4F  52 5F 54 41 ; _SGI.GL_COLOR_TA
00000550: 42 4C 45 5F  42 4C 55 45  5F 53 49 5A  45 00 47 4C ; BLE_BLUE_SIZE.GL
00000560: 5F 43 4F 4C  4F 52 5F 54  41 42 4C 45  5F 42 4C 55 ; _COLOR_TABLE_BLU
00000570: 45 5F 53 49  5A 45 5F 45  58 54 00 47  4C 5F 43 4F ; E_SIZE_EXT.GL_CO
00000580: 4C 4F 52 5F  54 41 42 4C  45 5F 42 4C  55 45 5F 53 ; LOR_TABLE_BLUE_S
00000590: 49 5A 45 5F  53 47 49 00  47 4C 5F 43  4F 4C 4F 52 ; IZE_SGI.GL_COLOR
000005A0: 5F 54 41 42  4C 45 5F 46  4F 52 4D 41  54 00 47 4C ; _TABLE_FORMAT.GL
000005B0: 5F 43 4F 4C  4F 52 5F 54  41 42 4C 45  5F 46 4F 52 ; _COLOR_TABLE_FOR
000005C0: 4D 41 54 5F  45 58 54 00  47 4C 5F 43  4F 4C 4F 52 ; MAT_EXT.GL_COLOR
000005D0: 5F 54 41 42  4C 45 5F 46  4F 52 4D 41  54 5F 53 47 ; _TABLE_FORMAT_SG
000005E0: 49 00 47 4C  5F 43 4F 4C  4F 52 5F 54  41 42 4C 45 ; I.GL_COLOR_TABLE
000005F0: 5F 47 52 45  45 4E 5F 53  49 5A 45 00  47 4C 5F 43 ; _GREEN_SIZE.GL_C
00000600: 4F 4C 4F 52  5F 54 41 42  4C 45 5F 47  52 45 45 4E ; OLOR_TABLE_GREEN
00000610: 5F 53 49 5A  45 5F 45 58  54 00 47 4C  5F 43 4F 4C ; _SIZE_EXT.GL_COL
00000620: 4F 52 5F 54  41 42 4C 45  5F 47 52 45  45 4E 5F 53 ; OR_TABLE_GREEN_S
00000630: 49 5A 45 5F  53 47 49 00  47 4C 5F 43  4F 4C 4F 52 ; IZE_SGI.GL_COLOR
00000640: 5F 54 41 42  4C 45 5F 49  4E 54 45 4E  53 49 54 59 ; _TABLE_INTENSITY
00000650: 5F 53 49 5A  45 00 47 4C  5F 43 4F 4C  4F 52 5F 54 ; _SIZE.GL_COLOR_T
00000660: 41 42 4C 45  5F 49 4E 54  45 4E 53 49  54 59 5F 53 ; ABLE_INTENSITY_S
00000670: 49 5A 45 5F  45 58 54 00  47 4C 5F 43  4F 4C 4F 52 ; IZE_EXT.GL_COLOR
00000680: 5F 54 41 42  4C 45 5F 49  4E 54 45 4E  53 49 54 59 ; _TABLE_INTENSITY
00000690: 5F 53 49 5A  45 5F 53 47  49 00 47 4C  5F 43 4F 4C ; _SIZE_SGI.GL_COL
000006A0: 4F 52 5F 54  41 42 4C 45  5F 4C 55 4D  49 4E 41 4E ; OR_TABLE_LUMINAN
000006B0: 43 45 5F 53  49 5A 45 00  47 4C 5F 43  4F 4C 4F 52 ; CE_SIZE.GL_COLOR
000006C0: 5F 54 41 42  4C 45 5F 4C  55 4D 49 4E  41 4E 43 45 ; _TABLE_LUMINANCE
000006D0: 5F 53 49 5A  45 5F 45 58  54 00 47 4C  5F 43 4F 4C ; _SIZE_EXT.GL_COL
000006E0: 4F 52 5F 54  41 42 4C 45  5F 4C 55 4D  49 4E 41 4E ; OR_TABLE_LUMINAN
000006F0: 43 45 5F 53  49 5A 45 5F  53 47 49 00  47 4C 5F 43 ; CE_SIZE_SGI.GL_C
00000700: 4F 4C 4F 52  5F 54 41 42  4C 45 5F 52  45 44 5F 53 ; OLOR_TABLE_RED_S
00000710: 49 5A 45 00  47 4C 5F 43  4F 4C 4F 52  5F 54 41 42 ; IZE.GL_COLOR_TAB
00000720: 4C 45 5F 52  45 44 5F 53  49 5A 45 5F  45 58 54 00 ; LE_RED_SIZE_EXT.
00000730: 47 4C 5F 43  4F 4C 4F 52  5F 54 41 42  4C 45 5F 52 ; GL_COLOR_TABLE_R
00000740: 45 44 5F 53  49 5A 45 5F  53 47 49 00  47 4C 5F 43 ; ED_SIZE_SGI.GL_C
00000750: 4F 4C 4F 52  5F 54 41 42  4C 45 5F 53  43 41 4C 45 ; OLOR_TABLE_SCALE
00000760: 00 47 4C 5F  43 4F 4C 4F  52 5F 54 41  42 4C 45 5F ; .GL_COLOR_TABLE_
00000770: 53 43 41 4C  45 5F 53 47  49 00 47 4C  5F 43 4F 4C ; SCALE_SGI.GL_COL
00000780: 4F 52 5F 54  41 42 4C 45  5F 57 49 44  54 48 00 47 ; OR_TABLE_WIDTH.G
00000790: 4C 5F 43 4F  4C 4F 52 5F  54 41 42 4C  45 5F 57 49 ; L_COLOR_TABLE_WI
000007A0: 44 54 48 5F  45 58 54 00  47 4C 5F 43  4F 4C 4F 52 ; DTH_EXT.GL_COLOR
000007B0: 5F 54 41 42  4C 45 5F 57  49 44 54 48  5F 53 47 49 ; _TABLE_WIDTH_SGI
000007C0: 00 47 4C 5F  43 4F 4C 4F  52 5F 57 52  49 54 45 4D ; .GL_COLOR_WRITEM
000007D0: 41 53 4B 00  47 4C 5F 43  4F 4D 42 49  4E 45 00 47 ; ASK.GL_COMBINE.G
000007E0: 4C 5F 43 4F  4D 42 49 4E  45 34 00 47  4C 5F 43 4F ; L_COMBINE4.GL_CO
000007F0: 4D 42 49 4E  45 5F 41 4C  50 48 41 00  47 4C 5F 43 ; MBINE_ALPHA.GL_C
00000800: 4F 4D 42 49  4E 45 5F 41  4C 50 48 41  5F 41 52 42 ; OMBINE_ALPHA_ARB
00000810: 00 47 4C 5F  43 4F 4D 42  49 4E 45 5F  41 4C 50 48 ; .GL_COMBINE_ALPH
00000820: 41 5F 45 58  54 00 47 4C  5F 43 4F 4D  42 49 4E 45 ; A_EXT.GL_COMBINE
00000830: 5F 41 52 42  00 47 4C 5F  43 4F 4D 42  49 4E 45 5F ; _ARB.GL_COMBINE_
00000840: 45 58 54 00  47 4C 5F 43  4F 4D 42 49  4E 45 5F 52 ; EXT.GL_COMBINE_R
00000850: 47 42 00 47  4C 5F 43 4F  4D 42 49 4E  45 5F 52 47 ; GB.GL_COMBINE_RG
00000860: 42 5F 41 52  42 00 47 4C  5F 43 4F 4D  42 49 4E 45 ; B_ARB.GL_COMBINE
00000870: 5F 52 47 42  5F 45 58 54  00 47 4C 5F  43 4F 4D 50 ; _RGB_EXT.GL_COMP
00000880: 41 52 45 5F  52 5F 54 4F  5F 54 45 58  54 55 52 45 ; ARE_R_TO_TEXTURE
00000890: 00 47 4C 5F  43 4F 4D 50  41 52 45 5F  52 5F 54 4F ; .GL_COMPARE_R_TO
000008A0: 5F 54 45 58  54 55 52 45  5F 41 52 42  00 47 4C 5F ; _TEXTURE_ARB.GL_
000008B0: 43 4F 4D 50  49 4C 45 00  47 4C 5F 43  4F 4D 50 49 ; COMPILE.GL_COMPI
000008C0: 4C 45 5F 41  4E 44 5F 45  58 45 43 55  54 45 00 47 ; LE_AND_EXECUTE.G
000008D0: 4C 5F 43 4F  4D 50 49 4C  45 5F 53 54  41 54 55 53 ; L_COMPILE_STATUS
000008E0: 00 47 4C 5F  43 4F 4D 50  52 45 53 53  45 44 5F 41 ; .GL_COMPRESSED_A
000008F0: 4C 50 48 41  00 47 4C 5F  43 4F 4D 50  52 45 53 53 ; LPHA.GL_COMPRESS
00000900: 45 44 5F 41  4C 50 48 41  5F 41 52 42  00 47 4C 5F ; ED_ALPHA_ARB.GL_
00000910: 43 4F 4D 50  52 45 53 53  45 44 5F 49  4E 54 45 4E ; COMPRESSED_INTEN
00000920: 53 49 54 59  00 47 4C 5F  43 4F 4D 50  52 45 53 53 ; SITY.GL_COMPRESS
00000930: 45 44 5F 49  4E 54 45 4E  53 49 54 59  5F 41 52 42 ; ED_INTENSITY_ARB
00000940: 00 47 4C 5F  43 4F 4D 50  52 45 53 53  45 44 5F 4C ; .GL_COMPRESSED_L
00000950: 55 4D 49 4E  41 4E 43 45  00 47 4C 5F  43 4F 4D 50 ; UMINANCE.GL_COMP
00000960: 52 45 53 53  45 44 5F 4C  55 4D 49 4E  41 4E 43 45 ; RESSED_LUMINANCE
00000970: 5F 41 4C 50  48 41 00 47  4C 5F 43 4F  4D 50 52 45 ; _ALPHA.GL_COMPRE
00000980: 53 53 45 44  5F 4C 55 4D  49 4E 41 4E  43 45 5F 41 ; SSED_LUMINANCE_A
00000990: 4C 50 48 41  5F 41 52 42  00 47 4C 5F  43 4F 4D 50 ; LPHA_ARB.GL_COMP
000009A0: 52 45 53 53  45 44 5F 4C  55 4D 49 4E  41 4E 43 45 ; RESSED_LUMINANCE
000009B0: 5F 41 52 42  00 47 4C 5F  43 4F 4D 50  52 45 53 53 ; _ARB.GL_COMPRESS
000009C0: 45 44 5F 52  47 42 00 47  4C 5F 43 4F  4D 50 52 45 ; ED_RGB.GL_COMPRE
000009D0: 53 53 45 44  5F 52 47 42  41 00 47 4C  5F 43 4F 4D ; SSED_RGBA.GL_COM
000009E0: 50 52 45 53  53 45 44 5F  52 47 42 41  5F 41 52 42 ; PRESSED_RGBA_ARB
000009F0: 00 47 4C 5F  43 4F 4D 50  52 45 53 53  45 44 5F 52 ; .GL_COMPRESSED_R
00000A00: 47 42 41 5F  46 58 54 31  5F 33 44 46  58 00 47 4C ; GBA_FXT1_3DFX.GL
00000A10: 5F 43 4F 4D  50 52 45 53  53 45 44 5F  52 47 42 41 ; _COMPRESSED_RGBA
00000A20: 5F 53 33 54  43 5F 44 58  54 31 5F 45  58 54 00 47 ; _S3TC_DXT1_EXT.G
00000A30: 4C 5F 43 4F  4D 50 52 45  53 53 45 44  5F 52 47 42 ; L_COMPRESSED_RGB
00000A40: 41 5F 53 33  54 43 5F 44  58 54 33 5F  45 58 54 00 ; A_S3TC_DXT3_EXT.
00000A50: 47 4C 5F 43  4F 4D 50 52  45 53 53 45  44 5F 52 47 ; GL_COMPRESSED_RG
00000A60: 42 41 5F 53  33 54 43 5F  44 58 54 35  5F 45 58 54 ; BA_S3TC_DXT5_EXT
00000A70: 00 47 4C 5F  43 4F 4D 50  52 45 53 53  45 44 5F 52 ; .GL_COMPRESSED_R
00000A80: 47 42 5F 41  52 42 00 47  4C 5F 43 4F  4D 50 52 45 ; GB_ARB.GL_COMPRE
00000A90: 53 53 45 44  5F 52 47 42  5F 46 58 54  31 5F 33 44 ; SSED_RGB_FXT1_3D
00000AA0: 46 58 00 47  4C 5F 43 4F  4D 50 52 45  53 53 45 44 ; FX.GL_COMPRESSED
00000AB0: 5F 52 47 42  5F 53 33 54  43 5F 44 58  54 31 5F 45 ; _RGB_S3TC_DXT1_E
00000AC0: 58 54 00 47  4C 5F 43 4F  4D 50 52 45  53 53 45 44 ; XT.GL_COMPRESSED
00000AD0: 5F 54 45 58  54 55 52 45  5F 46 4F 52  4D 41 54 53 ; _TEXTURE_FORMATS
00000AE0: 00 47 4C 5F  43 4F 4E 53  54 41 4E 54  00 47 4C 5F ; .GL_CONSTANT.GL_
00000AF0: 43 4F 4E 53  54 41 4E 54  5F 41 4C 50  48 41 00 47 ; CONSTANT_ALPHA.G
00000B00: 4C 5F 43 4F  4E 53 54 41  4E 54 5F 41  4C 50 48 41 ; L_CONSTANT_ALPHA
00000B10: 5F 45 58 54  00 47 4C 5F  43 4F 4E 53  54 41 4E 54 ; _EXT.GL_CONSTANT
00000B20: 5F 41 52 42  00 47 4C 5F  43 4F 4E 53  54 41 4E 54 ; _ARB.GL_CONSTANT
00000B30: 5F 41 54 54  45 4E 55 41  54 49 4F 4E  00 47 4C 5F ; _ATTENUATION.GL_
00000B40: 43 4F 4E 53  54 41 4E 54  5F 42 4F 52  44 45 52 5F ; CONSTANT_BORDER_
00000B50: 48 50 00 47  4C 5F 43 4F  4E 53 54 41  4E 54 5F 43 ; HP.GL_CONSTANT_C
00000B60: 4F 4C 4F 52  00 47 4C 5F  43 4F 4E 53  54 41 4E 54 ; OLOR.GL_CONSTANT
00000B70: 5F 43 4F 4C  4F 52 5F 45  58 54 00 47  4C 5F 43 4F ; _COLOR_EXT.GL_CO
00000B80: 4E 53 54 41  4E 54 5F 45  58 54 00 47  4C 5F 43 4F ; NSTANT_EXT.GL_CO
00000B90: 4E 56 4F 4C  55 54 49 4F  4E 5F 31 44  00 47 4C 5F ; NVOLUTION_1D.GL_
00000BA0: 43 4F 4E 56  4F 4C 55 54  49 4F 4E 5F  32 44 00 47 ; CONVOLUTION_2D.G
00000BB0: 4C 5F 43 4F  4E 56 4F 4C  55 54 49 4F  4E 5F 42 4F ; L_CONVOLUTION_BO
00000BC0: 52 44 45 52  5F 43 4F 4C  4F 52 00 47  4C 5F 43 4F ; RDER_COLOR.GL_CO
00000BD0: 4E 56 4F 4C  55 54 49 4F  4E 5F 42 4F  52 44 45 52 ; NVOLUTION_BORDER
00000BE0: 5F 43 4F 4C  4F 52 5F 48  50 00 47 4C  5F 43 4F 4E ; _COLOR_HP.GL_CON
00000BF0: 56 4F 4C 55  54 49 4F 4E  5F 42 4F 52  44 45 52 5F ; VOLUTION_BORDER_
00000C00: 4D 4F 44 45  00 47 4C 5F  43 4F 4E 56  4F 4C 55 54 ; MODE.GL_CONVOLUT
00000C10: 49 4F 4E 5F  42 4F 52 44  45 52 5F 4D  4F 44 45 5F ; ION_BORDER_MODE_
00000C20: 45 58 54 00  47 4C 5F 43  4F 4E 56 4F  4C 55 54 49 ; EXT.GL_CONVOLUTI
00000C30: 4F 4E 5F 46  49 4C 54 45  52 5F 42 49  41 53 00 47 ; ON_FILTER_BIAS.G
00000C40: 4C 5F 43 4F  4E 56 4F 4C  55 54 49 4F  4E 5F 46 49 ; L_CONVOLUTION_FI
00000C50: 4C 54 45 52  5F 42 49 41  53 5F 45 58  54 00 47 4C ; LTER_BIAS_EXT.GL
00000C60: 5F 43 4F 4E  56 4F 4C 55  54 49 4F 4E  5F 46 49 4C ; _CONVOLUTION_FIL
00000C70: 54 45 52 5F  53 43 41 4C  45 00 47 4C  5F 43 4F 4E ; TER_SCALE.GL_CON
00000C80: 56 4F 4C 55  54 49 4F 4E  5F 46 49 4C  54 45 52 5F ; VOLUTION_FILTER_
00000C90: 53 43 41 4C  45 5F 45 58  54 00 47 4C  5F 43 4F 4E ; SCALE_EXT.GL_CON
00000CA0: 56 4F 4C 55  54 49 4F 4E  5F 46 4F 52  4D 41 54 00 ; VOLUTION_FORMAT.
00000CB0: 47 4C 5F 43  4F 4E 56 4F  4C 55 54 49  4F 4E 5F 46 ; GL_CONVOLUTION_F
00000CC0: 4F 52 4D 41  54 5F 45 58  54 00 47 4C  5F 43 4F 4E ; ORMAT_EXT.GL_CON
00000CD0: 56 4F 4C 55  54 49 4F 4E  5F 48 45 49  47 48 54 00 ; VOLUTION_HEIGHT.
00000CE0: 47 4C 5F 43  4F 4E 56 4F  4C 55 54 49  4F 4E 5F 48 ; GL_CONVOLUTION_H
00000CF0: 45 49 47 48  54 5F 45 58  54 00 47 4C  5F 43 4F 4E ; EIGHT_EXT.GL_CON
00000D00: 56 4F 4C 55  54 49 4F 4E  5F 57 49 44  54 48 00 47 ; VOLUTION_WIDTH.G
00000D10: 4C 5F 43 4F  4E 56 4F 4C  55 54 49 4F  4E 5F 57 49 ; L_CONVOLUTION_WI
00000D20: 44 54 48 5F  45 58 54 00  47 4C 5F 43  4F 4F 52 44 ; DTH_EXT.GL_COORD
00000D30: 5F 52 45 50  4C 41 43 45  00 47 4C 5F  43 4F 4F 52 ; _REPLACE.GL_COOR
00000D40: 44 5F 52 45  50 4C 41 43  45 5F 41 52  42 00 47 4C ; D_REPLACE_ARB.GL
00000D50: 5F 43 4F 4F  52 44 5F 52  45 50 4C 41  43 45 5F 4E ; _COORD_REPLACE_N
00000D60: 56 00 47 4C  5F 43 4F 50  59 00 47 4C  5F 43 4F 50 ; V.GL_COPY.GL_COP
00000D70: 59 5F 49 4E  56 45 52 54  45 44 00 47  4C 5F 43 4F ; Y_INVERTED.GL_CO
00000D80: 50 59 5F 50  49 58 45 4C  5F 54 4F 4B  45 4E 00 47 ; PY_PIXEL_TOKEN.G
00000D90: 4C 5F 43 55  4C 4C 5F 46  41 43 45 00  47 4C 5F 43 ; L_CULL_FACE.GL_C
00000DA0: 55 4C 4C 5F  46 41 43 45  5F 4D 4F 44  45 00 47 4C ; ULL_FACE_MODE.GL
00000DB0: 5F 43 55 4C  4C 5F 56 45  52 54 45 58  5F 45 58 54 ; _CULL_VERTEX_EXT
00000DC0: 00 47 4C 5F  43 55 4C 4C  5F 56 45 52  54 45 58 5F ; .GL_CULL_VERTEX_
00000DD0: 45 59 45 5F  50 4F 53 49  54 49 4F 4E  5F 45 58 54 ; EYE_POSITION_EXT
00000DE0: 00 47 4C 5F  43 55 4C 4C  5F 56 45 52  54 45 58 5F ; .GL_CULL_VERTEX_
00000DF0: 4F 42 4A 45  43 54 5F 50  4F 53 49 54  49 4F 4E 5F ; OBJECT_POSITION_
00000E00: 45 58 54 00  47 4C 5F 43  55 52 52 45  4E 54 5F 41 ; EXT.GL_CURRENT_A
00000E10: 54 54 52 49  42 5F 4E 56  00 47 4C 5F  43 55 52 52 ; TTRIB_NV.GL_CURR
00000E20: 45 4E 54 5F  42 49 54 00  47 4C 5F 43  55 52 52 45 ; ENT_BIT.GL_CURRE
00000E30: 4E 54 5F 43  4F 4C 4F 52  00 47 4C 5F  43 55 52 52 ; NT_COLOR.GL_CURR
00000E40: 45 4E 54 5F  46 4F 47 5F  43 4F 4F 52  44 00 47 4C ; ENT_FOG_COORD.GL
00000E50: 5F 43 55 52  52 45 4E 54  5F 46 4F 47  5F 43 4F 4F ; _CURRENT_FOG_COO
00000E60: 52 44 49 4E  41 54 45 00  47 4C 5F 43  55 52 52 45 ; RDINATE.GL_CURRE
00000E70: 4E 54 5F 49  4E 44 45 58  00 47 4C 5F  43 55 52 52 ; NT_INDEX.GL_CURR
00000E80: 45 4E 54 5F  4D 41 54 52  49 58 5F 41  52 42 00 47 ; ENT_MATRIX_ARB.G
00000E90: 4C 5F 43 55  52 52 45 4E  54 5F 4D 41  54 52 49 58 ; L_CURRENT_MATRIX
00000EA0: 5F 49 4E 44  45 58 5F 41  52 42 00 47  4C 5F 43 55 ; _INDEX_ARB.GL_CU
00000EB0: 52 52 45 4E  54 5F 4D 41  54 52 49 58  5F 4E 56 00 ; RRENT_MATRIX_NV.
00000EC0: 47 4C 5F 43  55 52 52 45  4E 54 5F 4D  41 54 52 49 ; GL_CURRENT_MATRI
00000ED0: 58 5F 53 54  41 43 4B 5F  44 45 50 54  48 5F 41 52 ; X_STACK_DEPTH_AR
00000EE0: 42 00 47 4C  5F 43 55 52  52 45 4E 54  5F 4D 41 54 ; B.GL_CURRENT_MAT
00000EF0: 52 49 58 5F  53 54 41 43  4B 5F 44 45  50 54 48 5F ; RIX_STACK_DEPTH_
00000F00: 4E 56 00 47  4C 5F 43 55  52 52 45 4E  54 5F 4E 4F ; NV.GL_CURRENT_NO
00000F10: 52 4D 41 4C  00 47 4C 5F  43 55 52 52  45 4E 54 5F ; RMAL.GL_CURRENT_
00000F20: 50 41 4C 45  54 54 45 5F  4D 41 54 52  49 58 5F 41 ; PALETTE_MATRIX_A
00000F30: 52 42 00 47  4C 5F 43 55  52 52 45 4E  54 5F 50 52 ; RB.GL_CURRENT_PR
00000F40: 4F 47 52 41  4D 00 47 4C  5F 43 55 52  52 45 4E 54 ; OGRAM.GL_CURRENT
00000F50: 5F 51 55 45  52 59 00 47  4C 5F 43 55  52 52 45 4E ; _QUERY.GL_CURREN
00000F60: 54 5F 51 55  45 52 59 5F  41 52 42 00  47 4C 5F 43 ; T_QUERY_ARB.GL_C
00000F70: 55 52 52 45  4E 54 5F 52  41 53 54 45  52 5F 43 4F ; URRENT_RASTER_CO
00000F80: 4C 4F 52 00  47 4C 5F 43  55 52 52 45  4E 54 5F 52 ; LOR.GL_CURRENT_R
00000F90: 41 53 54 45  52 5F 44 49  53 54 41 4E  43 45 00 47 ; ASTER_DISTANCE.G
00000FA0: 4C 5F 43 55  52 52 45 4E  54 5F 52 41  53 54 45 52 ; L_CURRENT_RASTER
00000FB0: 5F 49 4E 44  45 58 00 47  4C 5F 43 55  52 52 45 4E ; _INDEX.GL_CURREN
00000FC0: 54 5F 52 41  53 54 45 52  5F 50 4F 53  49 54 49 4F ; T_RASTER_POSITIO
00000FD0: 4E 00 47 4C  5F 43 55 52  52 45 4E 54  5F 52 41 53 ; N.GL_CURRENT_RAS
00000FE0: 54 45 52 5F  50 4F 53 49  54 49 4F 4E  5F 56 41 4C ; TER_POSITION_VAL
00000FF0: 49 44 00 47  4C 5F 43 55  52 52 45 4E  54 5F 52 41 ; ID.GL_CURRENT_RA

```

---

### Post by ago on 2007-05-23
```

C:\>fstest dump C:10372960+8
00000000: 49 4E 44 58  28 00 09 00  00 00 00 00  00 00 00 00 ; INDX(...........
00000010: 00 00 00 00  00 00 00 00  28 00 00 00  70 05 00 00 ; ........(...p...
00000020: E8 0F 00 00  00 00 00 00  23 12 69 00  00 00 00 00 ; ........#.i.....
00000030: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000040: F3 52 00 00  00 00 38 00  80 00 6C 00  00 00 00 00 ; .R....8...l.....
00000050: 15 53 00 00  00 00 1D 00  00 B7 04 92  D8 9C C7 01 ; .S..............
00000060: 00 DB 28 24  35 7F C7 01  00 DB 28 24  35 7F C7 01 ; ..($5.....($5...
00000070: 00 91 A3 CA  D6 9C C7 01  00 60 06 00  00 00 00 00 ; .........`......
00000080: 02 52 06 00  00 00 00 00  00 00 00 00  00 00 00 00 ; .R..............
00000090: 15 00 61 00  62 00 69 00  2D 00 32 00  2E 00 36 00 ; ..a.b.i.-.2...6.
000000A0: 2E 00 32 00  30 00 2D 00  31 00 35 00  2D 00 67 00 ; ..2.0.-.1.5.-.g.
000000B0: 65 00 6E 00  65 00 72 00  69 00 63 00  00 00 00 00 ; e.n.e.r.i.c.....
000000C0: F4 52 00 00  00 00 4D 00  88 00 72 00  00 00 00 00 ; .R....M...r.....
000000D0: 15 53 00 00  00 00 1D 00  00 B7 04 92  D8 9C C7 01 ; .S..............
000000E0: 00 FD C4 94  1F 7F C7 01  00 FD C4 94  1F 7F C7 01 ; ................
000000F0: 80 20 6C 91  D8 9C C7 01  00 50 01 00  00 00 00 00 ; . l......P......
00000100: 22 45 01 00  00 00 00 00  00 00 00 00  00 00 00 00 ; "E..............
00000110: 18 00 63 00  6F 00 6E 00  66 00 69 00  67 00 2D 00 ; ..c.o.n.f.i.g.-.
00000120: 32 00 2E 00  36 00 2E 00  32 00 30 00  2D 00 31 00 ; 2...6...2.0.-.1.
00000130: 35 00 2D 00  67 00 65 00  6E 00 65 00  72 00 69 00 ; 5.-.g.e.n.e.r.i.
00000140: 63 00 00 00  00 00 00 00  16 53 00 00  00 00 10 00 ; c........S......
00000150: 60 00 4A 00  00 00 00 00  15 53 00 00  00 00 1D 00 ; `.J......S......
00000160: 80 E6 03 62  CD 9C C7 01  80 34 2A 7A  D2 9C C7 01 ; ...b.....4*z....
00000170: 80 34 2A 7A  D2 9C C7 01  00 D1 86 8D  CD 9C C7 01 ; .4*z............
00000180: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000190: 00 20 00 10  00 00 00 00  04 03 67 00  72 00 75 00 ; . ........g.r.u.
000001A0: 62 00 00 00  00 00 00 00  21 53 00 00  00 00 19 00 ; b.......!S......
000001B0: 60 00 4E 00  00 00 00 00  15 53 00 00  00 00 1D 00 ; `.N......S......
000001C0: 00 1E DF 92  C3 9C C7 01  00 1E DF 92  C3 9C C7 01 ; ................
000001D0: 00 1E DF 92  C3 9C C7 01  80 3A EE 8C  CD 9C C7 01 ; .........:......
000001E0: 00 10 79 00  00 00 00 00  08 0F 79 00  00 00 00 00 ; ..y.......y.....
000001F0: 20 20 00 00  00 00 00 00  06 03 69 00  6E 00 23 12 ;   ........i.n.#.
00000200: 74 00 72 00  64 00 74 00  F7 52 00 00  00 00 1E 00 ; t.r.d.t..R......
00000210: 90 00 7A 00  00 00 00 00  15 53 00 00  00 00 1D 00 ; ..z......S......
00000220: 00 B7 04 92  D8 9C C7 01  80 20 6C 91  D8 9C C7 01 ; ......... l.....
00000230: 80 20 6C 91  D8 9C C7 01  80 20 6C 91  D8 9C C7 01 ; . l...... l.....
00000240: 00 C0 73 00  00 00 00 00  F9 B3 73 00  00 00 00 00 ; ..s.......s.....
00000250: 00 00 00 00  00 00 00 00  1C 00 69 00  6E 00 69 00 ; ..........i.n.i.
00000260: 74 00 72 00  64 00 2E 00  69 00 6D 00  67 00 2D 00 ; t.r.d...i.m.g.-.
00000270: 32 00 2E 00  36 00 2E 00  32 00 30 00  2D 00 31 00 ; 2...6...2.0.-.1.
00000280: 35 00 2D 00  67 00 65 00  6E 00 65 00  72 00 69 00 ; 5.-.g.e.n.e.r.i.
00000290: 63 00 00 00  00 00 00 00  F8 52 00 00  00 00 1C 00 ; c........R......
000002A0: 98 00 82 00  00 00 00 00  15 53 00 00  00 00 1D 00 ; .........S......
000002B0: 00 B7 04 92  D8 9C C7 01  00 D9 CA 77  D8 9C C7 01 ; ...........w....
000002C0: 00 D9 CA 77  D8 9C C7 01  80 6F 63 78  D8 9C C7 01 ; ...w.....ocx....
000002D0: 00 00 6A 00  00 00 00 00  AD FC 69 00  00 00 00 00 ; ..j.......i.....
000002E0: 00 00 00 00  00 00 00 00  20 00 69 00  6E 00 69 00 ; ........ .i.n.i.
000002F0: 74 00 72 00  64 00 2E 00  69 00 6D 00  67 00 2D 00 ; t.r.d...i.m.g.-.
00000300: 32 00 2E 00  36 00 2E 00  32 00 30 00  2D 00 31 00 ; 2...6...2.0.-.1.
00000310: 35 00 2D 00  67 00 65 00  6E 00 65 00  72 00 69 00 ; 5.-.g.e.n.e.r.i.
00000320: 63 00 2E 00  62 00 61 00  6B 00 00 00  00 00 00 00 ; c...b.a.k.......
00000330: 22 53 00 00  00 00 0C 00  60 00 4C 00  00 00 00 00 ; "S......`.L.....
00000340: 15 53 00 00  00 00 1D 00  00 13 74 77  C3 9C C7 01 ; .S........tw....
00000350: 00 13 74 77  C3 9C C7 01  00 13 74 77  C3 9C C7 01 ; ..tw......tw....
00000360: 00 D1 86 8D  CD 9C C7 01  00 B0 1A 00  00 00 00 00 ; ................
00000370: CC A0 1A 00  00 00 00 00  20 20 00 00  00 00 00 00 ; ........  ......
00000380: 05 03 6C 00  69 00 6E 00  75 00 78 00  6F 00 74 00 ; ..l.i.n.u.x.o.t.
00000390: F9 52 00 00  00 00 22 00  70 00 5E 00  00 00 00 00 ; .R....".p.^.....
000003A0: 15 53 00 00  00 00 1D 00  80 4D 9D 92  D8 9C C7 01 ; .S.......M......
000003B0: 00 55 43 13  3D F4 C6 01  00 55 43 13  3D F4 C6 01 ; .UC.=....UC.=...
000003C0: 00 85 B3 1B  D7 9C C7 01  00 80 01 00  00 00 00 00 ; ................
000003D0: 88 71 01 00  00 00 00 00  00 00 00 00  00 00 00 00 ; .q..............
000003E0: 0E 00 6D 00  65 00 6D 00  74 00 65 00  73 00 74 00 ; ..m.e.m.t.e.s.t.
000003F0: 38 00 36 00  2B 00 2E 00  62 00 69 00  6E 00 23 12 ; 8.6.+...b.i.n.#.
00000400: 19 52 00 00  00 00 2D 00  90 00 7A 00  00 00 00 00 ; .R....-...z.....
00000410: 15 53 00 00  00 00 1D 00  80 20 6C 91  D8 9C C7 01 ; .S....... l.....
00000420: 80 98 7A 4E  35 7F C7 01  80 98 7A 4E  35 7F C7 01 ; ..zN5.....zN5...
00000430: 00 AD F1 D8  D6 9C C7 01  00 60 0C 00  00 00 00 00 ; .........`......
00000440: 1E 50 0C 00  00 00 00 00  00 00 00 00  00 00 00 00 ; .P..............
00000450: 1C 00 53 00  79 00 73 00  74 00 65 00  6D 00 2E 00 ; ..S.y.s.t.e.m...
00000460: 6D 00 61 00  70 00 2D 00  32 00 2E 00  36 00 2E 00 ; m.a.p.-.2...6...
00000470: 32 00 30 00  2D 00 31 00  35 00 2D 00  67 00 65 00 ; 2.0.-.1.5.-.g.e.
00000480: 6E 00 65 00  72 00 69 00  63 00 00 00  00 00 00 00 ; n.e.r.i.c.......
00000490: FA 52 00 00  00 00 1F 00  88 00 74 00  00 00 00 00 ; .R........t.....
000004A0: 15 53 00 00  00 00 1D 00  80 4D 9D 92  D8 9C C7 01 ; .S.......M......
000004B0: 00 DB 28 24  35 7F C7 01  00 DB 28 24  35 7F C7 01 ; ..($5.....($5...
000004C0: 00 91 A3 CA  D6 9C C7 01  00 B0 1A 00  00 00 00 00 ; ................
000004D0: CC A0 1A 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000004E0: 19 00 76 00  6D 00 6C 00  69 00 6E 00  75 00 7A 00 ; ..v.m.l.i.n.u.z.
000004F0: 2D 00 32 00  2E 00 36 00  2E 00 32 00  30 00 2D 00 ; -.2...6...2.0.-.
00000500: 31 00 35 00  2D 00 67 00  65 00 6E 00  65 00 72 00 ; 1.5.-.g.e.n.e.r.
00000510: 69 00 63 00  00 00 00 00  17 53 00 00  00 00 0F 00 ; i.c......S......
00000520: 60 00 50 00  00 00 00 00  15 53 00 00  00 00 1D 00 ; `.P......S......
00000530: 80 E6 03 62  CD 9C C7 01  00 D1 86 8D  CD 9C C7 01 ; ...b............
00000540: 00 D1 86 8D  CD 9C C7 01  00 D1 86 8D  CD 9C C7 01 ; ................
00000550: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000560: 00 20 00 10  00 00 00 00  07 03 77 00  69 00 6E 00 ; . ........w.i.n.
00000570: 62 00 6F 00  6F 00 74 00  00 00 00 00  00 00 00 00 ; b.o.o.t.........
00000580: 10 00 00 00  02 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000590: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000005A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000005B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000005C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000005D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000005E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000005F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 23 12 ; ..............#.
00000600: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000610: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000620: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000630: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000640: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000650: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000660: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000670: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000680: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000690: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000006A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000006B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000006C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000006D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000006E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000006F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000700: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000710: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000720: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000730: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000740: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000750: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000760: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000770: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000780: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000790: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000007A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000007B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000007C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000007D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000007E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000007F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 23 12 ; ..............#.
00000800: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000810: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000820: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000830: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000840: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000850: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000860: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000870: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000880: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000890: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000008A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000008B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000008C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000008D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000008E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000008F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000900: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000910: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000920: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000930: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000940: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000950: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000960: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000970: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000980: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000990: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000009A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000009B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000009C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000009D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000009E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000009F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 23 12 ; ..............#.
00000A00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000A90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000AA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000AB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000AC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000AD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000AE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000AF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000B90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000BA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000BB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000BC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000BD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000BE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000BF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 23 12 ; ..............#.
00000C00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000C90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000CA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000CB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000CC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000CD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000CE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000CF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000D90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000DA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000DB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000DC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000DD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000DE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000DF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 23 12 ; ..............#.
00000E00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000E90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000EA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000EB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000EC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000ED0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000EE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000EF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000F90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000FA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000FB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000FC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000FD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000FE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000FF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 23 12 ; ..............#.

```

---

### Post by ago on 2007-05-23
```


C:\>fstest -v inode C:\wubi\boot
00000000: 46 49 4C 45  00 00 00 00  00 00 8B 32  00 00 38 04 ; FILE.......2..8.
00000010: 1D 00 01 00  38 00 03 00  60 01 00 00  00 04 00 00 ; ....8...`.......
00000020: 00 00 00 00  00 00 00 00  06 00 00 00  15 53 00 00 ; .............S..
00000030: 04 1B 00 00  47 11 00 00  10 00 00 00  60 00 00 00 ; ....G.......`...
00000040: 00 00 00 00  00 00 00 00  48 00 00 00  18 00 00 00 ; ........H.......
00000050: 80 E6 03 62  CD 9C C7 01  80 34 2A 7A  D2 9C C7 01 ; ...b.....4*z....
00000060: 80 34 2A 7A  D2 9C C7 01  00 D1 86 8D  CD 9C C7 01 ; .4*z............
00000070: 00 20 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; . ..............
00000080: 00 00 00 00  6D 01 00 00  00 00 00 00  00 00 00 00 ; ....m...........
00000090: 00 00 00 00  00 00 00 00  20 00 00 00  48 00 00 00 ; ........ ...H...
000000A0: 01 00 40 00  00 00 03 00  00 00 00 00  00 00 00 00 ; ..@.............
000000B0: 00 00 00 00  00 00 00 00  40 00 00 00  00 00 00 00 ; ........@.......
000000C0: 00 10 00 00  00 00 00 00  B8 00 00 00  00 00 00 00 ; ................
000000D0: B8 00 00 00  00 00 00 00  31 01 EF 78  0D 00 00 00 ; ........1..x....
000000E0: A0 00 00 00  50 00 00 00  01 04 40 00  00 00 05 00 ; ....P.....@.....
000000F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000100: 48 00 00 00  00 00 00 00  00 10 00 00  00 00 00 00 ; H...............
00000110: 00 10 00 00  00 00 00 00  00 10 00 00  00 00 00 00 ; ................
00000120: 24 00 49 00  33 00 30 00  31 01 EC C8  13 00 00 00 ; $.I.3.0.1.......
00000130: B0 00 00 00  28 00 00 00  00 04 18 00  00 00 04 00 ; ....(...........
00000140: 08 00 00 00  20 00 00 00  24 00 49 00  33 00 30 00 ; .... ...$.I.3.0.
00000150: 01 00 00 00  00 00 00 00  FF FF FF FF  82 79 47 11 ; .............yG.
00000160: 02 52 06 00  00 00 00 00  00 00 00 00  00 00 00 00 ; .R..............
00000170: 15 00 61 00  62 00 69 00  2D 00 32 00  2E 00 36 00 ; ..a.b.i.-.2...6.
00000180: 2E 00 32 00  30 00 2D 00  31 00 35 00  2D 00 67 00 ; ..2.0.-.1.5.-.g.
00000190: 65 00 6E 00  65 00 72 00  69 00 63 00  00 00 00 00 ; e.n.e.r.i.c.....
000001A0: 16 53 00 00  00 00 10 00  60 00 4A 00  00 00 00 00 ; .S......`.J.....
000001B0: 15 53 00 00  00 00 1D 00  A0 97 63 62  CD 9C C7 01 ; .S........cb....
000001C0: 80 EB 9D 8D  CD 9C C7 01  80 EB 9D 8D  CD 9C C7 01 ; ................
000001D0: 80 EB 9D 8D  CD 9C C7 01  00 00 00 00  00 00 00 00 ; ................
000001E0: 00 00 00 00  00 00 00 00  00 20 00 10  00 00 00 00 ; ......... ......
000001F0: 04 03 67 00  72 00 75 00  62 00 00 00  00 00 00 00 ; ..g.r.u.b.......
00000200: 21 53 00 00  00 00 19 00  60 00 4E 00  00 00 00 00 ; !S......`.N.....
00000210: 15 53 00 00  00 00 1D 00  00 1E DF 92  C3 9C C7 01 ; .S..............
00000220: 00 1E DF 92  C3 9C C7 01  B0 33 25 8D  CD 9C C7 01 ; .........3%.....
00000230: B0 33 25 8D  CD 9C C7 01  00 10 79 00  00 00 00 00 ; .3%.......y.....
00000240: 08 0F 79 00  00 00 00 00  20 20 00 00  00 00 00 00 ; ..y.....  ......
00000250: 06 03 69 00  6E 00 69 00  74 00 72 00  64 00 74 00 ; ..i.n.i.t.r.d.t.
00000260: 22 53 00 00  00 00 0C 00  60 00 4C 00  00 00 00 00 ; "S......`.L.....
00000270: 15 53 00 00  00 00 1D 00  00 13 74 77  C3 9C C7 01 ; .S........tw....
00000280: 00 13 74 77  C3 9C C7 01  F0 55 99 8D  CD 9C C7 01 ; ..tw.....U......
00000290: F0 55 99 8D  CD 9C C7 01  00 B0 1A 00  00 00 00 00 ; .U..............
000002A0: CC A0 1A 00  00 00 00 00  20 20 00 00  00 00 00 00 ; ........  ......
000002B0: 05 03 6C 00  69 00 6E 00  75 00 78 00  6F 00 74 00 ; ..l.i.n.u.x.o.t.
000002C0: 19 52 00 00  00 00 2D 00  90 00 7A 00  00 00 00 00 ; .R....-...z.....
000002D0: 15 53 00 00  00 00 1D 00  80 20 6C 91  D8 9C C7 01 ; .S....... l.....
000002E0: 80 98 7A 4E  35 7F C7 01  80 98 7A 4E  35 7F C7 01 ; ..zN5.....zN5...
000002F0: 00 AD F1 D8  D6 9C C7 01  00 60 0C 00  00 00 00 00 ; .........`......
00000300: 1E 50 0C 00  00 00 00 00  00 00 00 00  00 00 00 00 ; .P..............
00000310: 1C 00 53 00  79 00 73 00  74 00 65 00  6D 00 2E 00 ; ..S.y.s.t.e.m...
00000320: 6D 00 61 00  70 00 2D 00  32 00 2E 00  36 00 2E 00 ; m.a.p.-.2...6...
00000330: 32 00 30 00  2D 00 31 00  35 00 2D 00  67 00 65 00 ; 2.0.-.1.5.-.g.e.
00000340: 6E 00 65 00  72 00 69 00  63 00 00 00  00 00 00 00 ; n.e.r.i.c.......
00000350: 17 53 00 00  00 00 0F 00  60 00 50 00  00 00 00 00 ; .S......`.P.....
00000360: 15 53 00 00  00 00 1D 00  A0 97 63 62  CD 9C C7 01 ; .S........cb....
00000370: 90 BA AE 8D  CD 9C C7 01  90 BA AE 8D  CD 9C C7 01 ; ................
00000380: 90 BA AE 8D  CD 9C C7 01  00 00 00 00  00 00 00 00 ; ................
00000390: 00 00 00 00  00 00 00 00  00 20 00 10  00 00 00 00 ; ......... ......
000003A0: 07 03 77 00  69 00 6E 00  62 00 6F 00  6F 00 74 00 ; ..w.i.n.b.o.o.t.
000003B0: 00 00 00 00  00 00 00 00  10 00 00 00  02 00 00 00 ; ................
000003C0: FF FF FF FF  82 79 47 11  00 00 00 00  00 00 00 00 ; .....yG.........
000003D0: 00 20 00 10  00 00 00 00  07 03 77 00  69 00 6E 00 ; . ........w.i.n.
000003E0: 62 00 6F 00  6F 00 74 00  00 00 00 00  00 00 00 00 ; b.o.o.t.........
000003F0: 10 00 00 00  02 00 00 00  FF FF FF FF  82 79 47 11 ; .............yG.
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $ATTRIBUTE_LIST (0x20) (nr,sz=184)
    7063416+8
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    10372960+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
Can't find 0x0 in attribute list

```

---

### Post by ago on 2007-05-23
> **bean123 said:**
> Yes, you can modify the preset menu with grubmenu:

grubmenu export grldr psmenu.lst

modify psmenu.lst, then

grubmenu import grldr psmenu.lst

The original preset menu is used to find menu.lst, you can change it to whatever you want.

That might be helpful for us as well to remove the root menu.lst which simply points to /wubi/boot/grub/menu.lst. PS any chance to have a flag to turn verbosity off?

Thanks in advance

---

### Post by tinybit on 2007-05-23
> **ago said:**
> PS any chance to have a flag to turn verbosity off?



The latest code in the svn tree has reduced the warnings by default. You can enable the warnings by executing a "debug on" command before hand.

---

### Post by bean123 on 2007-05-23
Try the new version, it should be working by now.

---

### Post by ago on 2007-05-23
Bean I am no longer at home, I'll do that tonight. Thanks again

---

### Post by ago on 2007-05-23
Almost there!!! Still some issues though: with an installation on a fat32 partition the find command enters into a loop

```

Booting 'Ubuntu'
find --set-root --ignore-floppies /wubi/boot/grub/menu.lst
(hd0,1) 
Filesystem type is ntfs, partition type 0x7
configfile /wubi/boot/grub/menu.lst
Turning on gate A20... Success.
Starting cmain()...

```

The last 2 lines flash very rapidly (probably because it loops)

The installation is actually in (hd0,6) which is a FAT32 partition, (hd0,1) is my ntfs partition where I USED to have the wubi installation, but it was uninstalled which in turns deleted  the folder.

It looks like grldr find command is tricked by the old deleted files. Let me know if you need any dump. 

I can manually select the root and then it works perfectly.

---

### Post by Temujin_12 on 2007-05-23
Are we still waiting for a fix for this?  I tried Wubi-7.04-test2 today using kubuntu 7.04 alternate and I still get the same error.

I ran 'contig -v -s c:\wubi\' and it reported fragmenting quite a few files.

UPDATE:
Using latest grldr.zip gets me past the 'error 17' but now I'm stuck here:
```
initrd /wubi/boot/initrd
  [Linux-initrd @ 0x1b74e000, 0x791177 bytes]
boot
Loading, please wait...
No RAID disks
```

After a long time (5-10 min.) I get the following:
```
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in-shell (ash)
Enter 'help' for a list of build-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```

---

### Post by Temujin_12 on 2007-05-23
Using latest grldr.zip gets me past the 'error 17' but now I'm stuck here:
```
initrd /wubi/boot/initrd
  [Linux-initrd @ 0x1b74e000, 0x791177 bytes]
boot
Loading, please wait...
No RAID disks
```

After a long time (5-10 min.) I get the following:
```
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in-shell (ash)
Enter 'help' for a list of build-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```

Bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106123](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106123) seems to indicate this is a kernel bug, but I'm not sure what to do from here.

---

### Post by ago on 2007-05-23
uninstall and reinstall
you can try [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield1.0.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield1.0.exe)

---

### Post by ecology2007 on 2007-05-23
To bean123 : 
I made a batch file that runs the fstest.exe and capture its output in fstest.txt, i suggest you modify it according your needs and ship it in each zip you post here.
I hope this will help you to gather relevant feedback.

```

@echo off



echo ------------------------------------------------------------------- 
echo This will :
echo uppgrade the wubi bootloader.
echo run some NTFS tests.
echo save them to fstest.txt.
echo You can safely close this windows if you want to abort.
echo ------------------------------------------------------------------- 
pause


echo ------------------------------------------------------------------- 
set /p DRIVAR=Which drive is wubi drive (If in doubt, type in "C:") ? 
set /p BOOTVAR=Which drive is boot drive (If in doubt, type in "C:") ? 

echo ------------------------------------------------------------------- 
echo Copy grldr to %BOOTVAR%\ %DRIVAR%\ and %DRIVAR%\wubi\boot\winboot\
echo Copy fstest.exe %DRIVAR%\wubi\boot\winboot\
copy grldr %DRIVAR%\wubi\boot\winboot\
copy fstest.exe %DRIVAR%\wubi\boot\winboot\
copy grldr %DRIVAR%\
echo Copy succesfull !

echo ------------------------------------------------------------------- 
echo Running fstest.exe !
del fstest.txt

echo ------------------------------------------------------------------- >> fstest.txt
echo fstest inode %DRIVAR%\wubi >> fstest.txt
echo ------------------------------------------------------------------- >> fstest.txt
fstest inode %DRIVAR%\wubi >> fstest.txt

echo ------------------------------------------------------------------- >> fstest.txt
echo inode %DRIVAR%\wubi\boot >> fstest.txt
echo ------------------------------------------------------------------- >> fstest.txt
fstest inode %DRIVAR%\wubi\boot >> fstest.txt

echo ------------------------------------------------------------------- >> fstest.txt
echo fstest -v inode %DRIVAR%\wubi\boot >> fstest.txt
echo ------------------------------------------------------------------- >> fstest.txt
fstest -v inode %DRIVAR%\wubi\boot >> fstest.txt

echo ------------------------------------------------------------------- >> fstest.txt
echo You can post the results here : "http://ubuntuforums.org/showthread.php?t=439965" >> fstest.txt
echo fstest.exe succesfull !



echo ------------------------------------------------------------------- 
echo Ouput is saved in fstest.txt.
echo You can post the the content of fstest.txt here :
echo "http://ubuntuforums.org/showthread.php?t=439965"
echo ------------------------------------------------------------------- 



pause


```

---

### Post by ago on 2007-05-23
> **Temujin_12 said:**
> 
Bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106123](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106123) seems to indicate this is a kernel bug, but I'm not sure what to do from here.
that'snot a grldr issue try to uninstall and install wubi again

---

### Post by alan53 on 2007-05-23
Been watching this thread for a while, just downloaded and installed minefield1.0 and got past the error 17, but now I have no xserver.  Message follows:

"Caught Signal 11.  Server aborting."

Investigation reveals," 'xserver-org' is not installed and no info is available"

---

### Post by bean123 on 2007-05-24
The problem should be fixed now, please verify.

Also add a script fstest.bat as suggested by ecology2007, anyone who have problem with NTFS can use it to generate basic debug information.

---

### Post by ago on 2007-05-24
Thanks bean, most efficient as usual!
And as usual I will try tonight and let you know. Your previous build is in minefield1.0

---

### Post by Temujin_12 on 2007-05-24
> **ago said:**
> uninstall and reinstall
you can try [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield1.0.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield1.0.exe)

Uninstalled then reinstalled using [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield1.0.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield1.0.exe) but this time I chose to use a 4GB partition instead of the default 6GB and the install finished :-) !!!!!  I'm now up in my Kubuntu 7.04 system!

---

### Post by ago on 2007-05-24
bean it does not loop and it does not show the last two lines (starting cmain), but it fails with Erro 17 when I run the find command.

Same setup as before, (hd0,1) is NTFS and used to contain old installation that was deleted (but a "trace" of old files might have been left over), (hd0,6) is FAT32 and contains actual installation.

---

### Post by bean123 on 2007-05-24
problem fixed, please test.

---

### Post by ago on 2007-05-24
Works great! Thanks a lot, amazing job, it's already in wubi.devel branch rev 79. Builds will come soon.

---

### Post by Computer Guru on 2007-05-25
I take it this is the final with regards to this bug?
Thanks Bean!

---

### Post by Computer Guru on 2007-05-25
Bean, is it possible to tell GRLDR.mbr to search for GRLDR in a **subdirectory**? (like C:\NST\GRLDR)
Would I have to change the code or is there a workaround for this?

The problem is that I'm going to have upwards of 20 "copies" of GRLDR, and my users would kill me if they found 20 files in C:\ :P

---

### Post by bean123 on 2007-05-25
The current grldr.mbr architecture only allows 3 (can be expanded to 4) sectors of NTFS code, therefore it's not practical to add more functionality. i'm planning to replace grldr.mbr with a more sophisticate boot loader. but it takes some time before it comes out.

---

### Post by Computer Guru on 2007-05-26
Yeah, I can understand why with the current size limitation and stuff.

Do you know if it is possible to load GRLDR directly with NTLDR, BCD, or GRUB?
I think I can take it from there.

---

### Post by rev.str on 2007-05-26
I have a Dell optiplex150 and installed ubuntu from the wubi installer. When I rebooted after installing ubuntu, I chose ubuntu from the boot menu. In the next screen I got  an error message saying cannot find GRLDR in all drives.

Harddisk is partitioned in one  NTFS  partition. 

Is there any solution to this problem?

Is there any linux drivers easily avaliable for my speedtouch 330 modem? My ISP is tiscali

---

### Post by tinybit on 2007-05-26
Insert a floppy with grldr and menu.lst in its root dir, and reboot.

Or wait for a fix on the bug.

---

### Post by bean123 on 2007-05-26
> **Computer Guru said:**
> Yeah, I can understand why with the current size limitation and stuff.

Do you know if it is possible to load GRLDR directly with NTLDR, BCD, or GRUB?
I think I can take it from there.

Yes, you can load another copy of grub4dos:

chainloader --force (hd0,0)/grldr

or

kernel (hd0,0)/grub.exe

---

### Post by ago on 2007-05-26
bean, tinybit are you around for a quick chat? pls send me a pm

---

### Post by tinybit on 2007-05-26
I am sorry I don't use any IM.

---

### Post by tinybit on 2007-05-26
> **bean123 said:**
> Yes, you can load another copy of grub4dos:

chainloader --force (hd0,0)/grldr

or

kernel (hd0,0)/grub.exe

At this moment, GNU GRUB does not support loading GRLDR with chainloader.

The "kernel (hd0,0)/grub.exe" should work with GNU GRUB.

Remember to type a boot command after the kernel line.

---

### Post by Computer Guru on 2007-05-27
Thanks, tinybit.

---

### Post by steve196 on 2007-05-28
Same thing here (windows 2000):
MBR Cylinders is not equal to BIOS one (several times)
Error 17 File not found.
The disk is larger that 137 Gbytes and the wubi files are likely beyond that limit, otherwise nothing unusual.

---

### Post by Sushubh on 2007-05-28
I no longer can boot into my Ubuntu installation. Here is what I end up with:

[[IMG]http://farm1.static.flickr.com/251/517592190_ab85190216.jpg[/IMG]]("http://flickr.com/photo_zoom.gne?id=517612307&size=m")

my wubi folder is in g:

[[IMG]http://farm1.static.flickr.com/196/517621189_c72a73c03d.jpg[/IMG]]("http://flickr.com/photo_zoom.gne?id=517621189&size=m")

---

### Post by ias on 2007-05-28
This may be this grub error 17 thing - I have no idea, and am new to linux and all. But maybe this helps:

Mldonkey (a p2p client I am running with the front-end 'sancho') needs to 'commit' files once they are finished downloading. At some point in this processes they are moved from a 'temp' to the default 'incoming' directory. To save space on my wubi linux side, i have the temp directory on the windows side while i couldn't work out how to move the 'incoming' directory, so it is on the linux side. you're not supposed to do that,  but well.

now, on 'committing' a 1.3 GB file, I suppose it began to copy the thing from the windows 'temp' dir to the linux 'incoming' dir. the whole thing crashed, and i could reboot either ubuntu feisty or windows xp. it gave the options, but just rebooted after i selected one of them.

after days of trying to correct things via live cd (disk not accessible) and ultimate boot cd etc etc, my tech guy at work simply did a chkdisk to clean up the filesystem which he says was somehow corrupted.

what happened? 

thanks for your help.

ias

---

### Post by ago on 2007-05-28
[Minefield 96-46](http://cutlersoftware.com/ubuntusetup/minefield.html) now includes latest grldr patches (28-may), that should take care of error 17. Many thanks to bean123 and tinybit for all their work.

---

### Post by steve196 on 2007-05-28
The patch recommended in the other thread did not do anything.

---

### Post by tuxcantfly on 2007-05-28
just merged in the other error 17 threads, no point in having multiple threads about the same error...

---

### Post by ecology2007 on 2007-05-28
This is a known bug, it should have been fixed.
We can't help you until you give details about your hard disks.
(Sizes, numbers of drives, where is windows, fat32, ntfs)...
Try this :
[http://ubuntuforums.org/showthread.php?t=457043](http://ubuntuforums.org/showthread.php?t=457043)

---

### Post by steve196 on 2007-05-28
Now i found, that the version i used (test2) should have fixed the error 17, so what i got is a new kind of error 17.
Does anyone else have the wubi files behind the 137 Gbyte mark?

---

### Post by ago on 2007-05-28
try [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by Squiggles on 2007-05-29
Hello All,

I'm having difficulty installing Wubi, since I get the prolonged "Loading, Please wait" error. I'm not sure what the error is, since it doesn't call any error code whatsoever.

Provided is a copy of the boot folder, minus initrd and linux. I'm trying to install xubuntu using wubi on an IBM Thinkpad 1161-94A series. It's currently installed under drive F, since C, D, or E are too small to use for this installation. I'm already using Minefield 96.46 for this. Boot.ini also was reset to the Windows default, and I can't seem to correctly fix this as well.

Requesting assistance on this matter.

Many thanks in advance.

---

### Post by ago on 2007-05-29
> **Squiggles said:**
> Hello All,

I'm having difficulty installing Wubi, since I get the prolonged "Loading, Please wait" error. I'm not sure what the error is, since it doesn't call any error code whatsoever.

That is probably not a grldr issue. You should edit c:\wubi\boot\grub\menu.lst and remove "quiet splash" wherever you see it. That should result in a more verbose output.

---

### Post by steve196 on 2007-05-29
"Now it shows its boot menu, but after that there is error 17. Somehow this grub never finds anything there is on drive J (which is a normal IDE HD with one ntfs partition, but larger than 137 GB)"


Fstest results:

------------------------------------------------------------------- 
fstest info j:\ 
------------------------------------------------------------------- 
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x20
------------------------------------------------------------------- 
fstest inode j:\$MFT 
------------------------------------------------------------------- 
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=98900992)
    32+32,256+193152
  $BITMAP (0xB0) (nr,sz=12080)
    16+8,86752536+8,273514496+8
------------------------------------------------------------------- 
fstest inode j:\wubi 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    wubi
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    185873384+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
------------------------------------------------------------------- 
fstest list j:\wubi\ 
------------------------------------------------------------------- 
0000031C             0  [boot]
00000AFB         17989  COPYING
0000006B             0  [disks]
000000BB             0  [docs]
000002B9             0  [install]
00000AF2         18326  license.txt
000000EA             0  [tools]
00002D42         77206  Uninstall.exe
00002D42         77206  UNINST~1.EXE
------------------------------------------------------------------- 
fstest inode j:\wubi\boot 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    boot
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=432)
------------------------------------------------------------------- 
fstest list j:\wubi\boot\ 
------------------------------------------------------------------- 
00000AEE             0  [grub]
00000AF4       7919067  initrd
00000AF7       1745100  linux
00000AF1             0  [winboot]
------------------------------------------------------------------- 
You can post the results here : "http://ubuntuforums.org/showthread.php?t=439965"

---

### Post by bean123 on 2007-05-29
The fstest.exe output seems fine, i think it's the 137G problem. grub uses int 13 to read disk, and some bios don't support reading beyond the 137G boundary.To fix it, you can installl wubi to another parition such as C:.

---

### Post by Squiggles on 2007-05-29
> **ago said:**
> That is probably not a grldr issue. You should edit c:\wubi\boot\grub\menu.lst and remove "quiet splash" wherever you see it. That should result in a more verbose output.
I checked the process when it booted, and I noticed it hangs on a certain memory address:

[   21.125537] Ohci_hcd 0000:00:14.0: irq 10, io mem 0x81c00000

any thoughts?

---

### Post by bean123 on 2007-05-29
Some thought on the 137G limit issue: maybe it can allow user to store startup files (kernel and initrd) in a seperate partition. once linux kernel is started, it's able to access the whole drive.

---

### Post by ago on 2007-05-29
> **Squiggles said:**
> I checked the process when it booted, and I noticed it hangs on a certain memory address:

[   21.125537] Ohci_hcd 0000:00:14.0: irq 10, io mem 0x81c00000

any thoughts?

That's a usb driver, if you use any usb device try to disconnect it.

---

### Post by ago on 2007-05-29
> **bean123 said:**
> Some thought on the 137G limit issue: maybe it can allow user to store startup files (kernel and initrd) in a seperate partition. once linux kernel is started, it's able to access the whole drive.

We can do that, but that should still involve some manual operation or an optional parameter, since we should not complicate the interface for everyone in order to cover a few corner cases. How common is this? I mean bios limitations? I would expect most bios today to be ready for larger disks.

---

### Post by Computer Guru on 2007-05-29
ago, I'm not sure, but doesn't forcing LBA - even if the BIOS doesn't support it - take care of this issue?

If I'm not mistaken, it's what current-gen Linux distros have an option for (Ubuntu-excluded) during GRUB setup. I've seen it on Fedora & Slackware.

---

### Post by ago on 2007-05-29
In grub-install it's a paramtere, I am not sure how to do that in grldr though, I am not a bootloader expert myserlf, you and bean123 know far more than I do on the topic.

---

### Post by Depressed Man on 2007-05-29
Could I get a zip or location of the latest one? I've tried most of the ones in this thread in the earlier posts and none of them resolve my err17. I used Wubi-7.04-minefield0.9.exe because I'm trying to do it on my Vista laptop. Now whenever I try to start ubuntu up it just gives me the error17 because of grub.

---

### Post by ago on 2007-05-29
[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by tinybit on 2007-05-29
> **ago said:**
> We can do that, but that should still involve some manual operation or an optional parameter, since we should not complicate the interface for everyone in order to cover a few corner cases. How common is this? I mean bios limitations? I would expect most bios today to be ready for larger disks.

I agree.

Only few BIOSes still have 137G limit. Even MS cannot solve this problem. MS only uses the first drive (0x80) for boot, and one of the 4 primary partitions. When MS builds a bootable drive, it confirms the bootable partition is accessible by BIOS; otherwise, it will issue error messages and do a repartitioning/reformating on the disk.

Technically, in a partition table, a partition's start-sector-number and its length can be 4 bytes long. So the partition table can handle disks as large as 2000GB.

On the other hand, EBIOS(sometimes also called LBA) uses 8 bytes(i.e., 64 bits) to locate a sector. So a (bug-free) EBIOS-machine can handle far larger disks than we could imagine for now. But, Most OSes only use 4 bytes for a sector number. So we may consider a 2000GB-disk as safe enough for both BIOS and OS.

---

### Post by bean123 on 2007-05-29
> **Computer Guru said:**
> ago, I'm not sure, but doesn't forcing LBA - even if the BIOS doesn't support it - take care of this issue?

If I'm not mistaken, it's what current-gen Linux distros have an option for (Ubuntu-excluded) during GRUB setup. I've seen it on Fedora & Slackware.

The lba option is only used in old style setup (stage* files), it instructs the loader to use LBA mode. The new loader grldr will use LBA by default, so you don't have to worry about that. But the 137G problem is caused by the size of LBA. old ATA/ATAPI specification uses 28-bit for lba, while the new one uses 48-bit. if the BIOS conforms to the old standard, then it's not possible to read beyond 137G before the protected mode driver is loaded.

---

### Post by tinybit on 2007-05-29
> **ago said:**
> In grub-install it's a paramtere, I am not sure how to do that in grldr though, I am not a bootloader expert myserlf, you and bean123 know far more than I do on the topic.

The simplest way might be by making duplicate copies of all the startup files(like grldr, menu.lst, linux kernel and initrd and such) in all partitions found. This can avoid creating a separate "boot" partition(like RedHat and Mandriva and many others).

---

### Post by ago on 2007-05-29
> **tinybit said:**
> The simplest way might be by making duplicate copies of all the startup files(like grldr, menu.lst, linux kernel and initrd and such) in all partitions found. This can avoid creating a separate "boot" partition(like RedHat and Mandriva and many others).

We were considering this route with ecology, but it's not feasible for kernel/initrd, since those have to be in a folder which is mounted under linux, or kernel upgrade is not possible.

---

### Post by ago on 2007-05-29
New release ([http://ubuntuforums.org/showthread.php?t=458607](http://ubuntuforums.org/showthread.php?t=458607) ) now includes latest bean123 patches and that should take care of error 17 & co.

---

### Post by Squiggles on 2007-05-30
> **ago said:**
> That's a usb driver, if you use any usb device try to disconnect it.

Hi Ago,

still doesn't work. there aren't any usb devices connected to the system.

---

### Post by steve196 on 2007-05-30
My problem was definitely the 137G limit. I now used a defragmenter, to move the wubi files to the beginning of the disk. Now install worked, but it created new files on the ntfs partition and reboot failed because linux was not found. Looks like a second round of the stupid defragger.

I think, wubi should be programmed to insist on writing its files, where GRUB can read them. Move some videos up if need be. Disks larger than 137G are becoming more and more common and the 137G problem is not obvious to most people.

---

### Post by Computer Guru on 2007-05-30
Here's the link to the latest GRLDR: [http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-28.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-28.zip)

EDIT: Didn't see page 14. Sorry.

---

### Post by Computer Guru on 2007-05-30
> **steve196 said:**
> My problem was definitely the 137G limit. I now used a defragmenter, to move the wubi files to the beginning of the disk. Now install worked, but it created new files on the ntfs partition and reboot failed because linux was not found. Looks like a second round of the stupid defragger.

I think, wubi should be programmed to insist on writing its files, where GRUB can read them. Move some videos up if need be. Disks larger than 137G are becoming more and more common and the 137G problem is not obvious to most people.

That's the point though - it **isn't** Wubi's fault.
Like the other posters menton, if you're using a newer (read: compatible) BIOS, it'll work just fine, 137GB or not.

This isn't a Wubi issue, it's a hardware-firmware limitation. See if there is an update for your BIOS.

It's totally overkill to have Wubi move sectors around the hard-drive and mess around with dangerous raw i/o apis just to ensure that those files are within the 137GB boundry - especially since most people with drives > 137GB have a bios that supports it.

---

### Post by Lugwalker on 2007-05-30
Not quite sure how to dump into the link you've given, but here's the result of the FSTEST:

------------------------------------------------------------------- 
fstest info c\ 
------------------------------------------------------------------- 
Invalid filename
------------------------------------------------------------------- 
fstest inode c\$MFT 
------------------------------------------------------------------- 
Invalid filename
------------------------------------------------------------------- 
fstest inode c\wubi 
------------------------------------------------------------------- 
Invalid filename
------------------------------------------------------------------- 
fstest list c\wubi\ 
------------------------------------------------------------------- 
Invalid filename
------------------------------------------------------------------- 
fstest inode c\wubi\boot 
------------------------------------------------------------------- 
Invalid filename
------------------------------------------------------------------- 
fstest list c\wubi\boot\ 
------------------------------------------------------------------- 
Invalid filename
------------------------------------------------------------------- 
You can post the results here : "http://ubuntuforums.org/showthread.php?t=439965"

---

### Post by bean123 on 2007-05-31
You are missing the ":". when asked for a directory, enter C: instead of C .

---

### Post by Lugwalker on 2007-05-31
Thanks, Bean123.  Here's the result:

------------------------------------------------------------------- 
fstest info C:\ 
------------------------------------------------------------------- 
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x627E90
------------------------------------------------------------------- 
fstest inode C:\$MFT 
------------------------------------------------------------------- 
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=137969664)
    6454928+40008,119680616+229464
  $BITMAP (0xB0) (nr,sz=16848)
    6454920+8,14249616+8,34366408+8,29336064+8,62656328+8
------------------------------------------------------------------- 
fstest inode C:\wubi 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    wubi
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    323568+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
------------------------------------------------------------------- 
fstest list C:\wubi\ 
------------------------------------------------------------------- 
0001C7D0             0  [boot]
00015654         17989  COPYING
0001C7C0             0  [disks]
0001C7C8             0  [docs]
0001C7CF             0  [install]
0001C808         18326  license.txt
000157E0          2968  README.txt
0001C7CC             0  [tools]
0001C86E         78744  Uninstall.exe
0001C86E         78744  UNINST~1.EXE
------------------------------------------------------------------- 
fstest inode C:\wubi\boot 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    boot
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=432)
------------------------------------------------------------------- 
fstest list C:\wubi\boot\ 
------------------------------------------------------------------- 
0001C7D6             0  [grub]
0001C810       7919247  initrd
0001C811       1745100  linux
0001C7D9             0  [winboot]
-------------------------------------------------------------------

---

### Post by bean123 on 2007-05-31
The output seems fine, what's the problem ?

---

### Post by Lugwalker on 2007-05-31
The boot gets this far and no further (sse attachment):

---

### Post by bean123 on 2007-05-31
I think this is not a grub related problem.

---

### Post by ago on 2007-05-31
Lugwalker run fdisk or equivalent to get rid of the first bunch of errors. You may want to use the latest minefield.

---

### Post by Computer Guru on 2007-05-31
lugwalker the easiest way to do it if you are on Vista, get [EasyBCD]("http://neosmart.net/dl.php?id=1"), go to the bootloader management section and press reinstall bootloader.

In XP boot from CD and type ```
fixmbr
fixboot
fixmbr
``` at the recovery console.

---

### Post by Lugwalker on 2007-05-31
> Bean123:
Lugwalker run fdisk or equivalent to get rid of the first bunch of errors.

Would running fdisk wipe my XP and all data from my computer?

Win XP Media Center edition
2.6Ghz Intel Pentium
1054mb ram
500gb hd

---

### Post by Computer Guru on 2007-05-31
Yes. But `fidisk /fixmbr` won't.

---

### Post by Lugwalker on 2007-05-31
Thanks, Guru.  So, if I go to 'Start-Run' in XP and type 'fidisk /fixmbr' then I'll not mess up anything?  Newbie speaking here :)

---

### Post by miketowninc on 2007-05-31
how long will it take to make hte bug fixs? so i can know to look for the answers or not

---

### Post by Lugwalker on 2007-05-31
These are the great mysteries of life, requiring endless patience :D

---

### Post by miketowninc on 2007-05-31
sounds great

---

### Post by Computer Guru on 2007-05-31
42

---

### Post by bean123 on 2007-06-01
fstest.exe update: detect reading beyond 137G

if you are reading beyond the 137G limit, fstest will print out a warning, and return 2 as error code.

fstest comp C:\grldr

fstest comp C:\wubi\boot\linux

fstest comp C:\wubi\boot\initrd

If all three commands complete without error or warning, it's likely that grub will be fine.

---

### Post by miketowninc on 2007-06-01
It didnt tell me if it worked or not but heres the txt.

---

### Post by Computer Guru on 2007-06-01
bean, has grldr been changed any in this last build?

---

### Post by bean123 on 2007-06-01
Yes, it improves the blocklist command. but this doesn't affect normal user.

---

### Post by Totally-Unwanted on 2007-06-01
I kept getting error 17 on Ubuntu startup, and found myself experimenting with the command lines and a floppy disk. From "C:/wubi/boot", I copied 3 files: 'grub', 'winboot', and 'grldr' onto the floppy, and took the --ignore-floppies command out of the line. Inserting the floppy before selecting Ubuntu from the startup menu solved my problem, but seeing as I've only tried it once, I can't be sure whether you have to edit the command lines on every boot ... I'll look into it.

---

### Post by bean123 on 2007-06-01
are you still getting error 17 with the latest vesion ? please generate debug dump with fstest.bat.

---

### Post by Computer Guru on 2007-06-01
Thanks bean. Excellent work as always.

---

### Post by miketowninc on 2007-06-01
I dont get what to do? And computer guru you did it and it worked?

---

### Post by Lugwalker on 2007-06-01
I just did a scan.  Does all seem well?  Thank you.
(Still can't get Ubuntu to get beyond the boot process, by the way)

------------------------------------------------------------------- 
fstest info "C:"\ 
------------------------------------------------------------------- 
part_start: 0x1F608
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x627E90
------------------------------------------------------------------- 
fstest inode "C:"\$MFT 
------------------------------------------------------------------- 
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=141541376)
    6454928+40008,119680616+236440
  $BITMAP (0xB0) (nr,sz=17280)
    6454920+8,14249616+8,34366408+8,29336064+8,62656328+8
Warning: reading beyond the 137G limit
------------------------------------------------------------------- 
fstest inode "C:"\. 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=68)
    .
  $OBJECT_ID (0x40) (r,sz=16)
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=280)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=12288)
    269041712+24
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
Warning: reading beyond the 137G limit
------------------------------------------------------------------- 
fstest list "C:"\ 
------------------------------------------------------------------- 
00003CB6          6112  dell.sdr
0000377C             0  [PROGRA~1]
000034B6             0  [Documents and Settings]
000034B6             0  [DOCUME~1]
00003B73             0  [drivers]
00020C76             0  [drvrtmp]
0000EB62             0  [f988bf71b8057fe5666a]
0000EB62             0  [F988BF~1]
0001D171             0  [Ghost Backups]
0001D171             0  [GHOSTB~1]
0001CCFE        178469  grldr
000015D8    1071685632  hiberfil.sys
00000011             0  [i386]
0000C9D4           480  ihsMAPI.ECF
0000D063          4128  INFCACHE.1
00003B70             0  IO.SYS
0000D546             0  [JB2Driver]
0000D546             0  [JB2DRI~1]
00016DC0       3993426  Kid does Canon on Guitar.gvi.MPC
00016DC0       3993426  KIDDOE~1.MPC
0001CCFD          1867  menu.lst
00015A45          1867  menu.lst.old
00015A45          1867  MENULS~1.OLD
00003B71             0  MSDOS.SYS
0000951D             0  [MSOCache]
000034B4         47564  NTDETECT.COM
000034B3        250032  ntldr
00015B0E    1607417856  pagefile.sys
0000377C             0  [Program Files]
00003B6F             0  AUTOEXEC.BAT
00016847             0  [Binaries]
000034B5           228  boot.ini
0000CDFC             0  [Brother]
00020D5E             0  [Config.Msi]
00003B6E             0  CONFIG.SYS
00003CB9             0  [dell]
00000B83             0  [RECYCLER]
0000D199            20  sccfg.sys
0001074A             0  [spoolerlogs]
0001074A             0  [SPOOLE~1]
00011408             0  [Start Menu]
00011408             0  [STARTM~1]
00003B72             0  [System Volume Information]
00003B72             0  [SYSTEM~1]
0000C37C             0  [temp]
00014F95          4096  VSNAP.IDX
00000B87             0  [WINDOWS]
0001C7BA             0  [wubi]
------------------------------------------------------------------- 
fstest inode "C:"\wubi 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    wubi
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    323568+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
Warning: reading beyond the 137G limit
------------------------------------------------------------------- 
fstest list "C:"\wubi\ 
------------------------------------------------------------------- 
0001C7D0             0  [boot]
00015654         17989  COPYING
0001C7C0             0  [disks]
0001C7C8             0  [docs]
0001C7CF             0  [install]
0001C808         18326  license.txt
000157E0          2968  README.txt
0001C7CC             0  [tools]
0001C86E         78744  Uninstall.exe
0001C86E         78744  UNINST~1.EXE
------------------------------------------------------------------- 
fstest inode "C:"\wubi\boot 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    boot
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=432)
Warning: reading beyond the 137G limit
------------------------------------------------------------------- 
fstest list "C:"\wubi\boot\ 
------------------------------------------------------------------- 
0001C7D6             0  [grub]
0001C810       7919247  initrd
0001C811       1745100  linux
0001C7D9             0  [winboot]
------------------------------------------------------------------- 
fstest comp "C:"\grldr 
------------------------------------------------------------------- 
File size : 178469
Comparing 
Succeed
Warning: reading beyond the 137G limit
------------------------------------------------------------------- 
fstest comp "C:"\wubi\boot\linux 
------------------------------------------------------------------- 
File size : 1745100
Comparing .
Succeed
Warning: reading beyond the 137G limit
------------------------------------------------------------------- 
fstest comp "C:"\wubi\boot\initrd 
------------------------------------------------------------------- 
File size : 7919247
Comparing .......
Succeed
Warning: reading beyond the 137G limit
-------------------------------------------------------------------

---

### Post by bean123 on 2007-06-01
You got the "reading beyond the 137G limit" warning, this means you must have a BIOS that supports large disk.

Defrag the partition, and run fstest.bat again, if the warning disappear, you are lucky. otherwise, you have to move startup files to a lower partition.

---

### Post by Lugwalker on 2007-06-02
Thanks, Bean.

---

### Post by bean123 on 2007-06-02
fstest.exe update:
* info command will show partition start sector and length.
* add parameter -q, if specified, fstest won't print anything. (quiet mode)

The return code of fstest:
0 : ok
1: warning (large lba)
2: error

---

### Post by ybark on 2007-08-27
foolishly, I changed my disk to dynamic disk 2 years ago for fun :-(, and I got the issue of "can't find menu.lst" when I finished wubi installation first step and reboot to Ubuntu.  The disk is 80G, partitions are c: d: e: f:
I don't want to delete the d: e: f:, so sure I can't get back to a basic disk.
if I can't install a non-vm Ubuntu without changing my disk?  Or some way can solve?

and here is the fstest.txt
------------------------------------------------------------------- 
fstest info f:\ 
------------------------------------------------------------------- 
version: 1.0 build 2
part_base: 0x1D (0M)
part_leng: 0x3362C5B (26309M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0xB3F70
------------------------------------------------------------------- 
fstest inode f:\#0 
------------------------------------------------------------------- 
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=88588288)
    737136+78656,825632+94368
  $BITMAP (0xB0) (nr,sz=10816)
    72688+16,19892560+8
------------------------------------------------------------------- 
fstest inode f:\#5 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=68)
    .
  $OBJECT_ID (0x40) (r,sz=16)
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=168)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=8192)
    14720848+16
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
------------------------------------------------------------------- 
fstest list f:\ 
------------------------------------------------------------------- 
0000001D             0  [SYSTEM~1]
00008003             0  [cygwin]
0000191D             0  [Emu8086v3.07]
0000191D             0  [EMU808~1.07]
000002E0             0  [for linux]
000002E0             0  [FORLIN~1]
000016A6             0  [ftp]
00008196             0  [games]
000011F8             0  [msdn2005]
000081A3    1609801728  pagefile.sys
000099A9             0  [RECYCLER]
0000001D             0  [System Volume Information]
0000001A             0  [Training]
00000C02             0  [wubi]
000081A2      10283097  Wubi-7.04.04.exe
000081A2      10283097  WUBI-7~1.EXE
000081A1             0  [wubi-save]
000081A1             0  [WUBI-S~1]
00008187        179352  wubildr
00008189          8192  wubildr.mbr
00000018             0  [&#21091;c]
------------------------------------------------------------------- 
fstest inode f:\wubi 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    wubi
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    72704+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
------------------------------------------------------------------- 
fstest list f:\wubi\ 
------------------------------------------------------------------- 
000080C0             0  [boot]
000011F5             0  [disks]
00004846             0  [docs]
000080B0             0  [install]
000080DC         18326  license.txt
000080F8          3057  README.txt
000080D6             0  [shared]
00004847             0  [tools]
000080DB         90786  wubi-uninstall.exe
000080DB         90786  WUBI-U~1.EXE
------------------------------------------------------------------- 
fstest inode f:\wubi\boot 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    boot
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=432)
------------------------------------------------------------------- 
fstest list f:\wubi\boot\ 
------------------------------------------------------------------- 
000080CC             0  [grub]
000080EA       7936165  initrd
000080EB       1745100  linux
000080D1             0  [winboot]
------------------------------------------------------------------- 
fstest comp f:\grldr 
------------------------------------------------------------------- 
ntfs_dir: 17
------------------------------------------------------------------- 
fstest comp f:\wubi\boot\linux 
------------------------------------------------------------------- 
File size : 1745100
Comparing .
Succeed
------------------------------------------------------------------- 
fstest comp f:\wubi\boot\initrd 
------------------------------------------------------------------- 
File size : 7936165
Comparing .......
Succeed
------------------------------------------------------------------- 
You can post the results here : "http://ubuntuforums.org/showthread.php?t=439965"

---

### Post by OrangeCrate on 2010-03-09
<deleted - wrong thread, sorry>

---


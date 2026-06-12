---
title: "Windows not booting following Ubuntu install"
date: 2014-05-20
forum: General Help
---

### Post by fenrizt2t on 2014-05-20
Hi 

I was really hoping someone on here might be able to help me as so far I've reached a real dead end.

I recently installed Ubuntu 14 on my computer which previosuly had windows 7 on it, with the aim of it being a dual boot system. I installed ubuntu in a 50gb partition on a 1tb disk. I know windows ran fine after creating the partition, but before the installation.

Anyway I then installed ubtuntu from a USB, and ubuntu now boots fine. However, when grub boots windows 7 is listed as an option, but when selected it only brings up a black screen with a flashing white cursor. I have checked with ubuntu and all the windws files are still there, so I don't think they were affected by the installation. For some reason though it seems maybe grub isn't linking to the correct boot files or something?

I've tried using a windows repair disk I downloaded, which simply says it cannot detect a problem. I have also run boot repair in ubuntu, but this hasn't fixed the problem. Following advice online I also downloaded test disk, but am not clear on how to use this to solve the issue.

Boot repair did give me an output which is here if anyone can make sense of it:

[http://paste.ubuntu.com/7484751/](http://paste.ubuntu.com/7484751/)

Thank you very much anyone who is able to help. 

Seb

---

### Post by oldfred on 2014-05-20
Windows has essential boot info in its PBR or partition boot sector. You installed grub to PBR. Testdisk may still say that is valid but in a NTFS partition it should not even be allowed. I think back with 10.10 we filed bug reports and they still let you install grub to a NTFS partition. They assume you know better, but many make that mistake.

```
 sda1: ________________________________

       File system:       [COLOR=#ff0000]ntfs[/COLOR]
    Boot sector type:  [COLOR=#ff0000]Grub2[/COLOR] (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 1928004136 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.


```

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by fenrizt2t on 2014-05-21
Sorry, I may be being dense.

I ran tesk disk as the link suggests and have got as far as selecting the windows drive, however, backupBS is not an option. My options are:

List
Rebuild BS
Repair MFT
Dump

Any idea why this is the case, or how I proceed?

---

### Post by oldfred on 2014-05-21
Have not seen that. But maybe you do not have the Backup BS?
If sda1 and that is your NTFS partition, run the Rebuild BS.

That will create a XP type Boot sector and you need to run chkdsk from a Windows repair CD or flash drive.

Windows will not run chkdsk or repair it with grub in the BS as it does not even see it as NTFS. But with a XP version in there then you can run chkdsk and it will update it to your version. Be sure to use a Windows 7 version of chkdsk as the XP version has ntldr inside it and Vista and newer have bootmgr inside them. That is how Windows knows which file to use to boot.

I ran a Windows 7 chkdsk on my XP install. It actually fixed some things that the XP chkdsk did not fix, but it converted BS to Windows 7 type and I have to convert it back with bootsect.exe on the Windows 7 repairCD.

---

### Post by fenrizt2t on 2014-05-21
I can the rebuild BS on the NTFS partition (the windows section). It gave the below:

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 115034 225  6 1848035328

filesystem size           1848035328 1848035321
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               48108646 48108646
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.



However, I then rebooted with a windows 7 repair disk as you suggested, and it still doesn't acknowledge there is any issue. Should I try using an XP repair disk?

Thank you so much for your help so far.

---

### Post by oldfred on 2014-05-21
I do not know or remember if in Testdisk you have to do a save to get it to remember the change?

Did the Windows 7 chkdsk run on sda1?

What then does BootInfo report show. It should not say the grub anymore if everything ran correctly.

---

### Post by fenrizt2t on 2014-05-21
I did tell testdisk to write, and it appeared to do so. The windows repair disk recognised the windows installation on sda1 and I ran it on that but it says it cannot find any erros to correct. 

I just ran another boot repair and the report is here:

[http://paste.ubuntu.com/7498681/](http://paste.ubuntu.com/7498681/)

---

### Post by fenrizt2t on 2014-05-21
Also there is no write option when I tell it to rebuildBS now, only list and dump

---

### Post by oldfred on 2014-05-21
Dump is is a compare of the backup and the current BS. I used that to compare my XP version after running chkdsk from Windows 7 and they were a lot different. But one near bottom said bootmgr and other ntldr, so I could tell that was a major difference.

You still show grub in PBR, so it did not change and then the Windows 7 chkdsk will not run. And I do not think the fixBoot which also is a repair to the Boot Sector with Windows does not run as it does not see a NTFS partition to repair.

When I do a dump on my old XP it tells me they are identical.

Using dump and scrolling down there is a line like this which shows NTLDR:

> 0198 63637572 72656400   ccurred.  63637572 72656400   ccurred.
01A0 0d0a4e54 4c445220   ..NTLDR   0d0a4e54 4c445220   ..NTLDR


If identical you get different choices, I see:

---

### Post by fenrizt2t on 2014-05-21
Yeah it says mine are identical. Do you know how I can fix this?

---

### Post by oldfred on 2014-05-21
You should be able to run the ReBuild BS and overwrite grub. If that is saved you will not have identical BS and will have the ntldr in the BS.
If it is not working is it giving an error message.

If you have the Windows 7 repair flash drive then you should be able to run this also, you want the newer one if using Windows 7:

 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by fenrizt2t on 2014-05-22
The test disk is still saying they are identical but is giving no error message and acting as if it has run. 

I tried the bootrec command on the repair disk, first mbr Then fix boot, it has clearly done something as Ubuntu will no longer boot, but windows won't either. Grub no longer loads, just a white flashing cursor on boot. I then tried the scanos command and it said it didn't find any windows installations.

Sorry to keep coming back with questions, but do you know why this may be.

---

### Post by slooksterpsv on 2014-05-22
Did you ever run chkdsk? Sometimes when it modifies for grub it can cause a corruption in the BITMAP file on the C: drive, you'll need to run a chkdsk in order to resolve this which can cause issues with it not starting. To run chkdsk do the following:

Boot from Windows 7 Recovery DVD
Choose Command Line from Advanced Options
Run (type into the command prompt): chkdsk /f C:

See if it fixes anything then try to reboot.

---

### Post by oldfred on 2014-05-22
Your fixMBR puts a Windows boot loader into the MBR to boot the Windows install in the NTFS partition with the boot flag. And that has to read the PBR. If it has grub in the Windows PBR, it may just boot into grub menu, but that is not correct. And then you can never boot Windows.

Just fixBoot usually has not worked as it does not seem to build a new boot sector, it may just restore a backup. Did you try bootsect.exe, I think that does create a brand new boot sector and it would be correct. Not sure now why testdisk will not build a new BS as that usually works.

Until you get grub out to the PBR or boot sector you will not have a working Windows.

---

### Post by fenrizt2t on 2014-05-22
Boostec did not get recognised as a command but bootrec seemed to create a new boot sector. Hence ubuntu wont now boot as grub doesn't boot on startup, the problem is that windows doesn't either, now I just get a flashing cursor. So I deleted grub but didn't replace it correctly, not sure how to do this last step. 

I have used a Ubuntu cd to reinstall the grub for now to get access to ubuntunagain and am now trying chkdsk

Any suggestions for a next step?

---

### Post by fenrizt2t on 2014-05-22
Check disk found no problems

---

### Post by oldfred on 2014-05-22
Does a new run of BootInfo show a normal Windows PBR or boot sector or is grub still in it?

If booting Windows form grub menu it may not work as grub really only boots working Windows. Some have gotten into f8 by pressing f8 at almost same time as grub entry for Windows, but those have to have a NTFS working PBR.

In the Windows repair it is bootsect.exe not bootsec.exe.
 [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by fenrizt2t on 2014-05-23
Thanks again both for the ongoing help.

I ran bootsect on C: following the instructions and it said it was succesfully updated to the target volume. Clearly again it did something, as grub has been removed. However, still not quite there as I again having the flashing white cursor, so hasn't enabled windows to boot.

I have another report from boot repair though here:

[http://paste.ubuntu.com/7504281/](http://paste.ubuntu.com/7504281/)

I don't know if this helps. I did again try running the windows repair automatic tool, and this still refuses to acknowledge the problem.

Do you think this is a solveable issue or am I going to need to re-purchase windows?

---

### Post by oldfred on 2014-05-23
From script it now looks normal and os-prober sees the boot files now, so it added a boot stanza.

Are you booting Windows from grub entry or from Windows in MBR?
 Best to try to resolve remaining issues by directly booting Windows from MBR as grub really only boots working Windows. And getting to repair console from grub requires hitting f8 at almost same time as grub menu entry where from MBR you have slightly more time.

I would run auto fixes three times and run chkdsk, if any errors rerun chkdsk. 
Beyond that I do not know what else to suggest.

---

### Post by slooksterpsv on 2014-05-23
When I had this issue, I had to follow a few different articles to get mine restored, one was similiar to this:
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

and this:
[http://www.tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/](http://www.tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/)

Try those two and see if you can get Windows to work. That way you can just reinstall Ubuntu.

---


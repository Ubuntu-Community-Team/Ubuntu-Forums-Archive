---
title: "Can't access Windows NTFS root partition... (DualBoot with Ubuntu 11.10)"
date: 2012-11-19
forum: General Help
---

### Post by 1grouchy on 2012-11-19
I have dual boot  Ubuntu 11.10/Windows 7 on my machine.

These days I got some errors with file system check when booting Ubuntu and solve that with running 'fsck' manual.

Today I needed  something to do on Win 7 and it won't boot. Instalation disk (Win7) sees HDD as one partition, Repair from disc didn't found any errors.

Command 'fdisk -l' shows partition where Windows is installed, also I can see partition in Nautilus, but I can't open it (Nautilus freeze).
/dev/sda1   *        2048   157288447    78643200    7  HPFS/NTFS/exFAT

Is there anyone who can help me with this.
Thanks in advance.

---

### Post by oldfred on 2012-11-19
If you just ran the Windows auto fix, you actually have to run it three times.

Did you run chkdsk? That often is most important.

Do you hibernate Windows when booting Ubuntu? Generally can lead to issues.

---

### Post by 1grouchy on 2012-11-20
> If you just ran the Windows auto fix, you actually have to run it three times.

Run Startup Repair for three times after I read you post. Nothing.
Windows did not found any problems... bla bla...


> Did you run chkdsk? That often is most important.

I run chkdsk, chkdsk /f, but the problem is that I run commands from DVD volume and i got error: Windows cannot run disk checking on this volume because it is write protected.

With command chkdsk C: /f /r /x tells me that there is no C: volume, and I cannot access to C:

Tried F8 after grub but nothing happens.


> Do you hibernate Windows when booting Ubuntu? Generally can lead to issues.

No, I'm sure.

When I try to mount sda1 (Win root) partition on Ubuntu with nautilus this is the error output:

[SIZE="2"][COLOR="DimGray"]Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=41490 count=1 br=-1: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.[/COLOR][/SIZE]


Tried this also:
sudo ntfsfix /dev/sda1

[COLOR="DimGray"]Mounting volume... ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=41490 count=1 br=-1: Input/output error
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Going to empty the journal ($LogFile)... OK
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=41490 count=1 br=-1: Input/output error
Remount failed: Input/output error[/COLOR]


Thanks for trying to help oldfred. Regards!

---

### Post by oldfred on 2012-11-20
ntfsfix only can do some minor repairs and usually turns on chkdsk flag so Windows runs chkdsk on next reboot. You need to be running chkdsk on partition with issues not any others.

Windows should be able to repair itself.

If you want to experiment.

       If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition 
small 'system reserved' NTFS partition instead of the partition where windows was installed. 

   Major MFT errors after NTFS partition move. - meierfra.
[http://ubuntuforums.org/showthread.php?t=1368432&highlight=grldr](http://ubuntuforums.org/showthread.php?t=1368432&highlight=grldr)

---

### Post by 1grouchy on 2012-11-21
New moments last night.

After I try ntfsfix with ntfs-3g package and that didn't work, I installed old ntfsprogs and try ntfsfix again, it fix partition to the point that I can now access to (sda1) with nautilus and C: from installation disc, still no booting Windows.

Startup Repair tool works for hours and give no results with booting Windows at the end. (I will try to run it couple more times today like you mention in your first post, last night was late for more)

chkdsk /f after that also worked hour/two same result. (I tried to reboot many times after chkdsk finished)

When mount sda1 in nautilus I can see after Start Repair and chkdsk processes files such as:

[SIZE="1"][COLOR="Gray"]eula.1028.txt, eula.1031.txt, eula.1033.txt, eula.1036.txt, eula.1040.txt, eula.1041.txt, eula.1042.txt, eula.2052.txt, eula.3082.txt, globdata.ini, install.exe, install.ini, install.res.1028.dll, install.res.1031.dll, install.res.1033.dll, install.res.1036.dll, install.res.1040.dll, install.res.1041.dll, install.res.1042.dll, install.res.2052.dll, install.res.3082.dll, VC_RED.cab, VC_RED.MSI, vcredist.bmp[/COLOR][/SIZE]

What do you think about rollback ntfs-3g now, after ntfsprogs fix sda1. It's newer, I don't know, maybe ntfsprogs gives me more headache in the future?

Also, if Startup Repair and chkdsk don't help me after few more tries, I will try with TestDisk and rebuilding MBR on C: partition as you mention.

Regards!

---

### Post by Mark Phelps on 2012-11-21
Given that filesystem check utilities are taking HOURS, and that you are encountering similar problems in both Windows and Linux, my best guess is that your hard drive is seriously failing.

The extremely long duration of chkdsk implies that the drive is trying over and over to read sectors that are on the fringe of failing.

Best thing you can do at this point is look into getting a new drive -- before this one crashes altogether.

---

### Post by 1grouchy on 2012-11-21
Many times in past when I clicked shutdown/restart on Ubuntu, he freeze on log out screen and than I needed to shutdown laptop by holding power button. Then I sympathize with HDD when I hear the sound of forced closure. :) That was made some Bad Sectors on HDD for sure.

Ubuntu freeze because of some networking problem. I don't know. Often ping goes to 5000ms and I need to restart card with:

[COLOR="DimGray"]sudo modprobe -r rtl8192se
sudo modprobe rtl8192se swenc=1[/COLOR]

Now I do shutdown/restart with following:

[COLOR="DimGray"]sudo /etc/init.d/networking stop
sudo shutdown -h now[/COLOR]
:)


I intend for months to buy some external HDD for backups (in our country, with a salary of 300€ and the cost of disk 100+ € not a small investment :), and you always have something more important to buy, pay...). Seems to me that I need a big trauma with loosing data to do that.

---

### Post by Mark Phelps on 2012-11-21
I certainly understand the cost problem ... but if the drive really is failing, the longer you delay, the worse it will become.  It could last another 6 months -- or it could die next week.

I had a 6-month old WD drive start to slow down like this, and within a week, it was unusable.

If you have a way to back off critical files to a USB stick, I would do that in the interim.

---

### Post by oldfred on 2012-11-21
Depending on what version of Ubuntu you are running you should not separately install ntfsfix.
       On April 12, 2011 it was announced that Ntfsprogs project was merged with NTFS-3G
[http://en.wikipedia.org/wiki/Ntfsprogs](http://en.wikipedia.org/wiki/Ntfsprogs)
# Do not do this as on newer versions it uninstalls ntfs-3g
sudo apt-get install ntfsprogs
man ntfsfix

    
If you cannot shutdown Ubuntu normally remember the elephants.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---


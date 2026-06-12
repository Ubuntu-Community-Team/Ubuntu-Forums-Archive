---
title: "Computer not starting"
date: 2019-05-29
forum: General Help
---

### Post by computernotworking on 2019-05-29
My computer, a Dell laptop which came with Ubuntu pre-installed, suddenly stopped booting.

Previously, Grub would automatically start Ubuntu, or if I pressed the escape key, Grub would offer me to run Ubuntu using an old kernel, restore Ubuntu to factory state or do a memory test.

Currently, a few error messages flash by, too quickly for me to read them. I filmed the screen with a camera and tried to decipher the text by pausing the film when the text appeared, but not all text was readable on the film. Question marks represent unreadable letters and numbers, and three question marks represent unreadable text of unknown length.

```
Could not open "\EFI\000?\fallback.efi": ??
Failed to open \EFI\000?\grub64.efi - long hexadecimal number
Failed to load image
Failed to open \EFI\0061\???.efi  long hexadecimal number
Failed to load image
```

After this, another message flashed by, also too fast to read it:

```
 Could not open "\EFI\000?\fallback.efi": ??
```

After this, I see text which stays on the screen long enough to be read, so I can read all of the text directly on the screen and don't need to rely on a partially unreadable film. I'm given two different options:

```
Dell Recovery
Dell Recovery (safe graphics mode)
```

Picking the first option, I see an Ubuntu logo on the screen. After some time, a minimal Busybox shell appears:

```
BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system
```

Any idea what I can do to make my computer boot again? I'm guessing that something has broken Grub, but I don't know how to fix this.

---

### Post by CatKiller on 2019-05-29
That looks most like hard drive failure to me. It's saying that it can't find the EFI, the first part of the bootstrapping process. If you've not done something to mess up your EFI, and it's happened spontaneously, hard drive failure is what I'd look at.

---

### Post by Rubi1200 on 2019-05-29
Hi and welcome to the forums :-)

I would suggest booting the computer with a liveUSB and checking what is going on.

You can create a boot summary (link in my signature) so we can take a closer look at what is there.

The message is not encouraging but let's hope we can try and fix things.

Definitely need to try and save your data from the live medium if possible.

Is there a warranty with the laptop and is it still valid? If yes, you can also contact Dell I believe and ask for support.

---

### Post by computernotworking on 2019-06-01
> **CatKiller said:**
> That looks most like hard drive failure to me.

This made me scared.

I booted into the computer using a live USB stick.

I was able to back up all of my files to an external memory using "dd if=/dev/sda3 of=/file/on/external/memory.img" so it was possible to read from the hard disk. I mounted the file using "-o loop,ro" and the checked a couple of files and confirmed that they looked correct. In other words, all of my files are safe. Also, "fdisk -l" was able to list all partitions.

I tried "sudo badblocks -v -o badblocks.txt /dev/sda 2> badblocks2.txt" which returned an empty badblocks.txt and a minimal badblocks2.txt:

```
Checking blocks 0 to 488386583
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
```

I tried the boot-info tool and this part of it surprised me:

```
Boot Info Summary: ===============================

 => **No boot loader is installed in the MBR of /dev/sda.**
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /factory/grubx64.efi /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /boot/grub/i386-pc/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

```

Is it normal that "No boot loader is installed in the MBR of /dev/sda"? Normally, my computer would boot from /dev/sda. Note that /dev/sdb is my live USB which I used for booting into my computer. It would normally not be inserted in my computer when using it.

```
Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda3, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file
```

Is this what I should try next? Other suggestions?

---

### Post by ajgreeny on 2019-06-01
The sentence **"No boot loader is installed in the MBR of /dev/sda"** is completely normal in a UEFI boot system, as grub is now installed by default in the EFI/ESP partition at sda1, as shown in the boot-info output, not to the MBR.

I am not sure about running the default repair as I do not use Windows any more and I am uncertain how the default repair deals with dual booting systems (you appear to have a Windows 8 installation as well as Ubuntu) so I suggest you wait to see if my colleague [COLOR="#FF0000"]oldfred[/COLOR] turns up; he will know much more than I do about boot-repair usage in a dual boot situation.

I suspect he will say you can run the default repair but I do not wish to tell you to do so, then find that I've messed up the Windows boot system for you.

---

### Post by computernotworking on 2019-06-02
> **ajgreeny said:**
> I am not sure about running the default repair as I do not use Windows any more and I am uncertain how the default repair deals with dual booting systems (you appear to have a Windows 8 installation as well as Ubuntu) so I suggest you wait to see if my colleague [COLOR=#FF0000]oldfred[/COLOR] turns up; he will know much more than I do about boot-repair usage in a dual boot situation.

I don't have any version of Windows installed. These are my partitions:

```
Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1026047   1024000   500M EFI System
/dev/sda2    1026048   7317503   6291456     3G Microsoft basic data
/dev/sda3    7317504 960358399 953040896 454.5G Linux filesystem
/dev/sda4  960358400 976771071  16412672   7.8G Linux swap
```

Although /dev/sda2 is listed as "Microsoft basic data", it seems to contain the files needed for restoring the original OS (Ubuntu 14.04) to its factory state. In any case, I think that 3 GB is too little space for any recent version of Windows.

---

### Post by Rubi1200 on 2019-06-02
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Is there a warranty with the laptop and is it still valid? If yes, you can also contact Dell I believe and ask for support.

And, have you explored this possible avenue?

---

### Post by computernotworking on 2019-06-02
> **Rubi1200 said:**
> And, have you explored this possible avenue?The manufacturer's voluntary warranty has expired, but there are a few months left of the vendor's statutory warranty. Dell is both the manufacturer and the vendor as the computer was bought from Dell's website. Since the statutory warranty is approaching the end, there is a shift in the burden of proof that it isn't my fault that the computer doesn't work, so I need better evidence that it isn't my fault before I can involve Dell. If I send Dell the computer, but Dell's inspection finds that it is my fault, then Dell will bill me for the shipping costs and investigation costs. I don't think it is my fault that the computer isn't working, but there's the problem with finding evidence one way or the other.

The risk that Dell claims that it is my fault (and bills me) needs to be considered against the effort of fixing the computer myself (if I can) and the cost of buying a new computer.

Someone suggested that the hard disk might be broken, but since "dd" was able to read the disk and since "badblocks" didn't find anything, I suspect that the error is something else. It is more likely that I can argue that it isn't my fault if it is a hardware problem than if it is a software problem.

---

### Post by TheFu on 2019-06-02
The Microsoft basic data is about the file system, nothing to do with Microsoft.  Probably a restore partition.

Over time, bits fail on storage.  badblocks will exercise the reading of the bits, but that isn't the same a flipping and re-writing the bits.  I would run a SMART test, wait a few hours for that to complete, then view the test results.  If everything in the SMART data seems fine, then I'd ensure my backups were working perfectly and wipe the disk, perform a fresh install using the current LTS release I want (which is still supported), then restore my data and OS settings.  Installing a minimal 18.04 desktop is about 12 minutes of effort.  Using dd makes an image.  Images aren't a good way to have efficient backups nor a good way to migrate to a new OS.  File-based backups are much better at that.

---

### Post by computernotworking on 2019-06-02
> **TheFu said:**
> 

Over time, bits fail on storage.  badblocks will exercise the reading of the bits, but that isn't the same a flipping and re-writing the bits.  I would run a SMART test, wait a few hours for that to complete, then view the test results.  If everything in the SMART data seems fine, then I'd ensure my backups were working perfectly and wipe the disk, perform a fresh install using the current LTS release I want (which is still supported), then restore my data and OS settings.  Installing a minimal 18.04 desktop is about 12 minutes of effort.

So I tried "smartctl -t long /dev/sda". Was this the correct test? It says that the test passed, so can I assume that the disk is fine?

```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.18.0-15-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD ***...
Device Model:     TOSHIBA ***
Serial Number:    ***
LU WWN Device Id: ***
Firmware Version: ***
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Jun  2 19:24:41 2019 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  120) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 123) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 128
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1330
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       7171
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       3673
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       39
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       319
193 Load_Cycle_Count        0x0032   093   093   000    Old_age   Always       -       70330
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       31 (Min/Max 14/48)
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0032   083   083   000    Old_age   Always       -       6808
241 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       8633306065
242 Total_LBAs_Read         0x0032   100   100   000    Old_age   Always       -       12656245420
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      7170         -
# 2  Short offline       Aborted by host               70%      4258         -
# 3  Short offline       Completed without error       00%         0         -
# 4  Short offline       Aborted by host               30%         0         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

> **TheFu said:**
> Using dd makes an image.  Images aren't a good way to have efficient backups nor a good way to migrate to a new OS.  File-based backups are much better at that.

I considered some of the differences between "rsync" and "dd":
[LIST]
[*]"dd" duplicates all space while "rsync" only copies used space, so "dd" uses up more space than "rsync", but I had lots of free space on the external HDD, so I didn't see this as a problem.
[*]"dd" requires restarting from the beginning when you want an updated backup, but "rsync" only copies over changed and new files, so "rsync" is a lot faster if you need to update your backup copy. When people wrote that the HDD might be broken, I thought that I potentially only would back up my computer once and then send it away to get a new HDD, so I didn't see any benefit here. With a new (or wiped) HDD, I'd just move /home and maybe some other directories over from the backup to the new installation.
[*]"dd" duplicates everything, but "rsync" has special options for symlinks, recursive copying and other things, so I felt that "dd" was safer in case I'd accidentally use an "rsync" flag which would skip something.
[/LIST]
Is there anything else I should have considered?

---

### Post by CatKiller on 2019-06-02
> **computernotworking said:**
> It says that the test passed, so can I assume that the disk is fine? 
No. 
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1330
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
```

It's saying that it's already having trouble reading, and that it's got a bunch of sectors that can't be used any more.

Edit: actually, looking at the raw values, possibly it doesn't say that.

But being able to complete a SMART test definitely doesn't mean the drive is fine. I'll let someone else interpret the output for you.

---

### Post by oldfred on 2019-06-02
You say system was pre-installed with 14.04. But that is now end of standard support in April 2019.
Extended support can be purchased. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---


---
title: "Drive not recognized after attempting dual boot"
date: 2014-11-08
forum: General Help
---

### Post by cary.stothart on 2014-11-08
Hello,

I was attempting to dual boot Windows 7 and Ubuntu on an HP laptop, and did something that made my 1 TB hard drive no longer recognizable to either BIOS or Ubuntu.  When I boot my computer now, it hangs on a black screen.  If I press Esc, it shows something like "Esc..Pause Startup" and hangs.  However, I can still access BIOS and Ubuntu (from USB) by pressing Esc and then Enter on startup.

In Ubuntu, sudo fdisk -l does not show the hard drive, but Disks shows it under disk drives as a 1 TB hard disk with the assessment: "disk is OK, one bad sector."

Here's how I came to this issue:

1) In Windows, I deleted the HP_Tools partition.
2) Shrank the C partition by 100 GB.
3) Restarted, booted Ubuntu from USB, opened gparted and created a 15 GB unformated partition.

Could you tell me how I can fix this?

Thanks!

---

### Post by yancek on 2014-11-08
> Could you tell me how I can fix this?

Do you know what the "something" you did is?  Hard to make suggestions on what to change when we don't know what was changed.  Did you ever get started with the Ubuntu installation?  Did you complete the install?  How many hard drives do you have?  Can you see your partitions using GParted?  Can you boot windows?

---

### Post by cary.stothart on 2014-11-08
I'm not able to boot Windows and I only have one hard drive.  When I start gparted, it shows that it's scanning all devices and then gives me an error after a few minutes: "Input/output error during read on /dev/sda." I also didn't complete the install. I stopped everything after finding out that Windows wont load and that BIOS cannot find my hard drive.

I ran into this issue after completing #3 above.  After I created a new unformated 15 GB partition with gparted and restarted my computer, I got and continue to get a black screen.  Also, pressing Esc and then Shift (not Enter as I said above) upon startup does not seem reliable as it takes me a number of times of restarting and pressing these keys before the menu containing the BIOS and boot locations appears.

---

### Post by cary.stothart on 2014-11-08
Also, if I click "Ignore" to the gparted error, the program will show a single unallocated 931.51 GiB partition.

---

### Post by westie457 on 2014-11-08
> [COLOR=#000000]Disks shows it under disk drives as a 1 TB hard disk with the assessment: "disk is OK, one bad sector."[/COLOR]

I hope that one bad sector is not at the start of the drive. If it is then no OS can be installed to the drive. The drive will only be okay for storage.

```
sudo badblocks -s /dev/sda
``` will locate and show where they are.

Substitute sda for sd<whatever drive you want to check>


If the one bad sector is not found within 5 minutes abort badblocks with Ctrl+C. Badblocks could take about 3 days to fully check a 1TB hard drive.

---

### Post by oldfred on 2014-11-08
Did you boot into Windows immediately after the resize. It has to run chkdsk to make repairs for its new size.

And the Linux NTFS driver will not mount a NTFS partition that needs chkdsk. I would use your Windows repairCD or flash drive to run chkdsk if you did not already run it.

---

### Post by cary.stothart on 2014-11-08
Thanks.  I started running badblocks and have so far recieved the following output:

buntu@ubuntu:~$ sudo badblocks -s /dev/sda
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 err
0 0.00% done, 0:09 elapsed. (0/0/0 errors)
1 0.00% done, 0:11 elapsed. (1/0/0 errors)
2 0.00% done, 0:14 elapsed. (2/0/0 errors)
3 0.00% done, 0:17 elapsed. (3/0/0 errors)
800.00% done, 0:20 elapsed. (4/0/0 errors)
810.00% done, 0:22 elapsed. (5/0/0 errors)
820.00% done, 0:24 elapsed. (6/0/0 errors)
...
546241% done, 18:09 elapsed. (452/0/0 errors)

I'm not sure how to read this.  I researched badblocks a bit and found that the first number in #/#/# represent read errors, but I don't know how to determine where on the drive the bad sector is from this.  I also found that this program can take dozens of hours to complete.  Does what I have so far tell me what I need to know, or do I need to let the program complete?

---

### Post by westie457 on 2014-11-08
You may as well stop badblocks. From that output I'm not sure where the error is either. The last time I used badblocks - well over a year ago - the command was in a different format with different output for progress. Give me some time to find the one I used then give that a try.


Might as well forget that. The command I was thinking of is used for something else and is **definitely not** to be used on your hard drive. Remembered it was for zeroing out a failing drive using 'dd'. That listed over 2000 bad sectors and zeroed out most of the drive.

---

### Post by oldfred on 2014-11-08
May notes show this as a command:
 sudo badblocks -wsv /dev/sdXY

And that is a partition not a drive like sda where X is drive and Y is partition.

See 
man badblocks

---

### Post by cary.stothart on 2014-11-08
@oldfred - I attempted to boot Windows after partitioning, but got a black screen upon startup.  Also, I ran chkdisk from a Windows 7 recovery disk and got: "Cannot open volume for direct access."  Not sure if this helps, but the recovery disk was also unable to find my Windows installation.

@westie457 - Thank you very much for your help.

---

### Post by oldfred on 2014-11-08
Windows may not recognize its own NTFS partition if it does not have boot flag, or if the partition boot sector is corrupted. 
May be best to just see all the details on where you are at. Boot-Repair cannot fix most Windows issues, but the summary report will show if configuration at least looks ok. Post link it gives.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cary.stothart on 2014-11-09
Thanks to everyone for the help so far.

I ran badblocks -wsv /dev/sdXY overnight and got:

...
545425513
545425514
badblocks: Unknown code ext2 70 adding to in-memory bad block list

This morning, I ran Boot Repair using a 64bit session (I have a 64 bit processor) and was told "Boot successfully repaired."  However, when I boot my computer now, I get "disk error, press any key to restart."  The link it gave me is [http://paste.ubuntu.com/8901349](http://paste.ubuntu.com/8901349).

---

### Post by oldfred on 2014-11-09
Your partition table is totally corrupted. All Boot-Repair did was add a boot flag as it saw that was missing but could not do anything else.

I might try testdisk to see if it can see old partitions, but if bad block was in partition table that could be the cause or just hard drive is failing/failed. 
Does in Disks (14.04) or Disk Utility(12.04) the Smart Status show drive is ok?  In Disks you click on the small gear in upper right corner to open advanced options.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by cary.stothart on 2014-11-09
In Disks, my hard drive is now listed under "Other Devices" and the gear in the upper right  corner only has the options: Format, Create Disk Image, Restore Disk Image, and Benchmark.  Is the option I need "SMART Data & Self-Tests?"  That option appears to be available if the drive is listed under "Disk Drives."  I don't know how I can make my drive be listed under that.

---

### Post by oldfred on 2014-11-09
BIOS has to correctly see drive for operating system to know it is available. Usually if BIOS does not see it, nothing in the operating system will see anything. So I do not understand other devices?
It seems BIOS sees something, but not a drive?

I have seen partition tables like yours where a user use dd to copy ISO to a drive or just started using drive as data without partitioning. Then the drive is a super floppy as it has no partition table and is just one very large floppy drive. Random data then is in first sector or sector 0 and the tools that try to read partition table see the random data and try to make it partition table data.

Perhaps erasing the first sector?  This would be all boot code and partition table info.
We are getting to the point where whatever we do may make it worse. Do you have good backups. If not I would image the hard drive to another drive so any repairs that do not work have a way to recover from.
Did you try testdisk yet?

Change sdX to your drive, must be sure it is correct. See below for caution on dd.
double check that you have correct drive.
       dd if=/dev/zero of=/dev/sdX bs=512 count=1


 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---


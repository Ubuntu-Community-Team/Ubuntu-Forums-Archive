---
title: "Boot Problems"
date: 2018-06-21
forum: General Help
---

### Post by SciFiFan on 2018-06-21
Although  I have been using Ubuntu for around 10 years, I don't do anything on  the programming side and only copy/paste things others have done. That  means that while I know what terminal is, I know next to nothing of how  to actually use it or programs to be used with it.


My  computer system is a custom desktop Qotom i7-4510U laptop processor  with a 64GB SSD, a 1 TB western digital hard drive and 16 GB of memory.  Attempting to format a 4TB USB Fantom external hard drive, I used the  Disks utility in Ubuntu 16.04 LTS (64 bit). The drive appeared in the  list, I clicked on it and then the gear icon. There, I clicked on 'Edit  mount options" as everything else was greyed out. I tried a few things  and nothing was working as I thought it should and must have clicked on  "OK" instead of "Cancel" Computer will not boot and goes to Emergency  Mode.


After  using the Boot-Repair application, a box appeared at the end stating an  error had occurred along with a message to boot on:

            sda1/EFI/ubuntu/shim64.efi

I could not find or did not know where to look for this to boot on. It wasn't in the BIOS list of things to boot with. 
[http://paste.ubuntu.com/p/GsR6mBtMwM/](http://paste.ubuntu.com/p/GsR6mBtMwM/)

What do I do next?

---

### Post by yancek on 2018-06-21
Some computer will have a boot option to boot "From EFI file" so I would look for that.  You have an EFI/GPT system and the proper EFI files for Ubuntu and your grub.cfg looks correct.
Did you have the 4TB drive plugged in when you ran boot repair as your output does not show any sign of it?
Edit mount options is not going to format a drive partition.  You should be using GParted to do that and you should be able to do it from the installed Ubuntu on an external drive.  You need to make sure the drive/partitions are not mounted.

Not knowing what "the few things" you tried are is going to make resolving this issue difficult.  Do you have your Ubuntu install DVD/usb drive available?

---

### Post by SciFiFan on 2018-06-21
When I was in the Disks part, all I did was turn "Automatic mount options" to OFF. Then I was entering some names but wasn't sure of anything so I erased them and left them blank. That was when I must have clicked on "OK" instead of "Cancel".

In the "Boot Options" part of my BIOS, I have tried everything that is there.

In the "Emergency Mode" and looking at the logs, I saw: mnt-sdc.mount: Mount process exited. code=exited status=32
                                                                                   Failed to mount/mnt/sdc
                                                                                   Dependency failed for Local File Systems

I have been using the Live usb for the last week.

---

### Post by SciFiFan on 2018-06-21
Reran Boot-Repair with external drive plugged in. It is not formatted.
[http://paste.ubuntu.com/p/VFRwcKRX25/](http://paste.ubuntu.com/p/VFRwcKRX25/)

In BIOS under Boot Override, I have the following options:
UEFI OS (P0: SATA SSD)
ubuntu OS (P0: SATA SSD)
ubuntu (P0: SATA SSD)
P0: SATA SSD
P2: WDC WD10JPVX-75JC3T0
VerbatimSTORE N GO 2.66
HP ENVY 7640 series 1.00
Generic Sorage Device 9451

---

### Post by oldfred on 2018-06-21
It is not showing a 4TB drive anywhere??

You have this in fstab, comment it out or remove it. You normally do not mount a drive, but mount a formatted partition.
       /dev/sdc /mnt/sdc auto sw 0 0 

And since referring to sdc, it may try to mount external drive or flash drive or whatever drive is currently seen as sdc. Best to use UUID to mount partitions. And you do not normally mount external devices with fstab, as when not available/unplugged system may not boot. You could use noauto parameter to load if available and but still have to mount with sudo if desire.

With large drive, you must use gpt partitioning. And I do not like to have one very large partition as more difficult to backup, or attempt to repair if issues. And I like to have an install on every drive, just for emergency use. So I always make an ESP - efi system partition (FAT32) as first partition and bios_grub (1MB) unformatted as second partition. And then 1 or more 25GB partitions for a smaller install.

I have seen others with issues with Disks, better to change to gpt, partition and format with gparted or gdisks. Make sure you are working on correct drive.
      
  Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or
sudo parted -l  # to know drive numbering
sudo parted /dev/sdX mklabel gpt # where sdX is correct drive, always double check first.
      
 [URL="http://www.rodsbooks.com/gdisk/"]http://www.rodsbooks.com/gdisk/

[/URL]

---

### Post by SciFiFan on 2018-06-21
oldfred;
Thank you for the reply, but how do I do the things you said?

---

### Post by yancek on 2018-06-21
Since you are working with an external drive, you can boot your installed Ubuntu and download and install GParted if you do not have it instaled

> sudo apt install gparted  

Or you can install it from the Software Manager.  ONce installed, you open in from a terminal with:  sudo gparted and you will see the graphical screen and follow the instruction by oldfred above.

---

### Post by SciFiFan on 2018-06-21
OK, I tried to explain in my very first posting on this thread that while I know what "terminal" is, I do not know how to program or edit something. I do have gparted available on the Live USB and have looked at it, but know nothing about how to use it. When opening gparted I get a message: "The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes". All I see on gparted is /dev/sda2/

---

### Post by oldfred on 2018-06-21
I think it is the upper right corner where you choose which drive you are working on.

       Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[https://gparted.org/news.php](https://gparted.org/news.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

The error is when gparted reads the USB flash drive or DVD, and you can ignore it.

---

### Post by oldfred on 2018-06-28
You asked for more info on gparted which we wanted to see if it showed your external drive.
Otherwise if we cannot see your external drive, it is a bigger issue.

And if not sure how to comment a line out in fstab, you just need to ask. Some users know more than others, so we do not duplicate very detailed instructions when all they need to know is issue and a direction. If you need more details, we can also provide that.

To edit fstab, you have to be a superuser or need to use sudo.
Everyone has nano editor but it is old school and you have to use arrow keys to move around and combination of keys to save or exit.
And where you mount fstab makes a difference. If inside your install it is at /etc/fstab.
But if using live installer you have to mount it first, otherwise you may be trying to edit the fstab in the live installer which cannot be edited.

       sudo mount /dev/sda2 /mnt
sudo nano /mnt/etc/fstab 
Then arrow down to this line and put a # at beginning of line. Anything with a # is a comment & ignored. Then save file. Keys to press are at bottom of window in nano.

You have multiple drives, so you do have to pay attention to which drive you are working on.
Plugging in a flash drive or unplugging it, may change which drive is sda, sdb etc.
Always know your drives and run this to confirm which is which.
sudo parted -l
or 
sudo fdisk -lu

---

### Post by SciFiFan on 2018-06-28
Thank you oldfred. In the very first post on this thread, I tried to explain that while I have used ubuntu for over 10 years, I am a complete novice. It just seemed that everyone was talking waaaayyy over my head.

Originally, I was trying to use the Disks utility to format the external 4 TB external hard drive and that is where I ran into problems. The drive remains unformatted. It shows up in gparted as /dev/sdc1 with an exclamation point in a red circle. That exclamation point is not explained anywhere in the documentation you provided. 

sda is a 64 Gb SSD
sdb is a 1 TB internal hard drive
sdc is where I have the problem

yancek was the one that brought up gparted. I never mentioned it in my posts until post #8.

---

### Post by SciFiFan on 2018-06-28
Not understanding what you said in #10. I should go to sudo mount /dev/sda2 /mnt and comment that out with nano?
sdc is where the problem is

---

### Post by oldfred on 2018-06-28
The red icon indicates a problem.
But if you right click on it, it will explain what the issue is.
But summary report from Boot-Repair showed sdc as iso9660?
Did you use dd to copy Ubuntu installer to your flash drive, but really copied to your large drive?
Did you have a lot of data on that large drive? If so the first 2GB was erased.

Your fstab is in sda2 per report and that seems to be another issue? and just needs minor editing.

If you did copy ISO to your 4TB drive, it will show errors as an ISO is a hybrid type configuration, not normal partitions.
You often then have to use dd to erase beginning of the drive, so then it can be partitioned. And as a very large drive, you must use gpt partitioning.

You probably need to use these instructions to erase beginning of drive.
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

---

### Post by SciFiFan on 2018-06-29
Back in **2016**, I used the Google Easy Linux Tips webpage to install Ubuntu 16.04 to the primary SSD and used the Western Digital 1 TB internal hard drive as storage. The instructions here on "Ubuntu Forums" were very confusing. Everything worked very nice for over two years.
In early June of **2018**, I bought a Fantom 4 TB and tried to use the Disks utility to format it. 
After clicking on the gear icon, I clicked on "Edit Mount Options" There I turned the "Automatic Mount Options" to "OFF". I tried a few things but nothing worked as I thought and must have clicked on "OK" instead of "CANCEL".

The new Fantom 4 TB external hard drive remains unformatted. It is plugged in via the USB 3.0 cable to a USB 3.0 port. Other than that, NOTHING has been done to it.
The system will not boot and goes to "Emergency Mode". Reading the system logs in "Emergency Mode" I saw that:
 mnt-sdc.mount: Mount process exited, code=exited status=32 
Failed to mount /mnt/sdc
This is highlighted in red.

I have been using my Live USB on a Verbatim STORE N GO USB stick since it won't boot.

In the gparted, right clicking on the line where the red circle with exclamation point and then clicking on "Information" brings up a number of possibilities, one of which that it is unformatted, which it is.

---

### Post by oldfred on 2018-06-29
Did you comment out the mount of sdc in your fstab? Since you have issues with sdc, that mount in fstab is preventing system from booting.

And your sdc is showing as an ISO.
If no data to rescue, you need to do the post #13 instructions to erase beginning of drive.
It is better than using dd directly as it includes some checks to make sure you are erasing the correct drive. I find many times my /dev/sdb can change to /dev/sdc or vice-versa. Issue is that a flash drive when plugged in and your reboot, my become sda and then when unplugged and reboot it changes again.

Then gparted should let you partition drive.

---

### Post by SciFiFan on 2018-06-30
That has been the gist of this entire thread! 
I wanted to know how to delete that /dev/sdc/ that is causing the computer not to boot. I tried to explain this back in post #3 of this thread. 

Still haven't gotten clear instructions on how to do that. Have an idea now, but would like to have something more concrete. Do I do that in "Emergency Mode" or can I use terminal in "Emergency Mode"?

What is this "dd" that you refer to?

Can certainly understand the changing of devices when a USB flash drive is used or not on successive boots. That is a logic situation. However, that is not the case here as my two drives are hardwired internally and do not change. When I plug in a USB, then it changes dependent on what I have or how many are plugged in through the USB ports. Easily see where it would be confusing if one can't see the flash drive in the computer or if one forgets that it is there. I'm old, it happens often!

---

### Post by yancek on 2018-06-30
Commenting out the incorrect entry in /etc/fstab was expalined in post #10.  If you are booted into the installed Ubuntu system, you would simply enter the following in a terminal:

```
sudo nano /etc/fstab
```

If you prefer the default gedit text editor, replace 'nano' with 'gedit' (without quotes)  Then simply put a hash mark at the beginning of the line so it looks like the below entry.   Then run the mount command or reboot.  If you are using a Live Ubuntu on another disk, you need to use the other option explained in post #10 which involves mounting your Ubuntu partition first before editing or you will be editing the /etc/fstab on the Live Ubuntu which is pointless.

> #/dev/sdc /mnt/sdc auto sw 0 0

---

### Post by SciFiFan on 2018-06-30
I'll give it a try. Will report back if it works! Thank you.

---

### Post by SciFiFan on 2018-07-01
Yes, your help was greatly appreciated. Everything now appears as it was.

---


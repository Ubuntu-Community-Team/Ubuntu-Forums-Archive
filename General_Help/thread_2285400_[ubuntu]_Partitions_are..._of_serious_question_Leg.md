---
title: "[ubuntu] Partitions are... of serious question? Legacy installed Ubuntu 14.04 64-bit("
date: 2015-07-05
forum: General Help
---

### Post by KurtisOmega on 2015-07-05
[IMG]http://s11.postimg.org/6go20nlv7/Partitions.png[/IMG]


Thank you for joining me today on Ubuntu Forums, I am new to the forums, just as I am new to Linux. However dually note my experience in C++, Java, HTML, XHTML, CSS, aswell as PHP.
Technology is a beautiful thing isn't it. (:

I have just removed and replaced the PC's version of Windows 8.1, the previous owner donated the machine to me out of kindness. It unfortunately had 361 threats on the operating system, therefore I knew that it would be in my best opinion to just jump to the great community of Linux. Heard to many good things and researched quite a bit, but never took the initial action, I suppose. But, as of right now these partitions are leaving me in question. I do not know what more than likely configured the partitions, but after my fresh install of Ubuntu 14.04 64amd onto this 64 bit Dell Optiplex 7010. Quite decent PC, but of course it is being road blocked by these partitions.

I have been encountering a little problem because some actions I perform tell me that the path is to long, this of course is because of the Toshiba 500GB HDD I have internally.

I am unable to do anything with these partitions, other than 'ext4' has an ability to "Resize/Move", and Linux OS Partition has the ability to "Swapoff".

What can I do to correct my partitions?
I installed with UEFI but Terminal says it's installed Legacy mode. I can only boot to Ubuntu from the BIOS, which opens Legacy boot first thing on this model of Motherboard from Dell.

All replies will be greatly appreciated and taken into hard working consideration.
Thank you in advance (:

[EDIT 4:41PM GMT-5 US/CANADA EASTERN]


[IMG]http://s13.postimg.org/piy432xqd/Bootrepair.png[/IMG]

Here is a reference of Boot-Repair on this system.

[ORIGINAL POST RESUMES]


Signing off,

Omega

-[COLOR=#ff0000]**QUICK BUMP/MAIN UPDATE**[/COLOR]-


After that Boot-Repair, of course I was able to set the boot options and configure the system so that Ubuntu was able to boot, this is what I was not worried of.

The ERROR: "You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted."
That is obvious if you have read what I stated above in the main thread, these partitions are tamped with. This was most likely done from the previous owners misuse of Windows and the installations, let alone the PC in general (ignorance is bliss).

Please notify me of information resolving this issue of mine, it would be truly appreciated.
Thank you in advance (:



Signing off,

Omega

---

### Post by grahammechanical on 2015-07-05
By the way, we do not see the URL to the Boot Repair report. So, what you think is obvious to us is not in fact obvious because we cannot see the Boot Repair report. And from the screen shot I cannot see anything wrong with those partitions.

sda1 is necessary if we install Ubuntu in EFI mode. Windows 8.1 makes use of it. And so does Ubuntu when installed in EFI mode.
sda2 is the partition with Ubuntu in it. It takes up nearly all the disk space.
sda3 is the swap partition. Just under 4GB is a reasonable amount. It all depends on how much RAM is in the machine and whether you intend to hibernate the OS.

It is usual to have a few MBs of unallocated space after or between partitions. If  you want to resize any of those partitions then it is best to do so from a Ubuntu live session DVD or USB memory stick. All those partitions have a key icon at the left side. That means they are "mounted." You will have to "unmount" the partition to resize it. But do not try to resize sda2 while you are running Ubuntu. And the swap partition (sda3) needs to be "swapoff" otherwise you cannot resize it.

> I am unable to do anything with these partitions,

What are you thinking of doing to these partitions?

Regards.







Regards.

---

### Post by howefield on 2015-07-05
> **KurtisOmega said:**
> I am unable to do anything with these partitions, other than... What can I do to correct my partitions?

You can't work with mounted partitions, so use gparted from a Live CD.

---

### Post by KurtisOmega on 2015-07-05
[QUOTE=grahammechanical]
What are you thinking of doing to these partitions?

Regards.
[/QUOTE]

Manage them honestly, these partitions seem to have misc data from previous OS.


[QUOTE=howefield]
You can't work with mounted partitions, so use gparted from a Live CD.

[/QUOTE]

Attempting Live now, will edit further information.

I need to correctly Mount my partitions, they are mounted incorrectly, how can I fix this?

---

### Post by oldfred on 2015-07-06
Please attach screen shots, not post in line. You can easily attach with advanced editor and paperclip icon.

You do show a link to Boot-Repair's Summary report in one screen shot, but I cannot remember all those digits (part of old in oldfred). Post link for us to review configuration.

Boot-Repair post the issue on far from start of drive. I have yet to see an UEFI system need any fixes. It was a problem with very old BIOS and is still an issue with some USB drive installs.
I normally install to a 25GB / (root) partition and use rest of drive as /home or /mnt/data with all my data in the data partitions. Some very minor performance advantage with newer very large TB sized drives. Linux ext4 partition randomly write data anywhere inside partition. So boot files are scattered across drive increasing seek time. But with newer drives that is not really noticeable.

---

### Post by KurtisOmega on 2015-07-06
-**[COLOR=#ff0000]QUICK BUMP/MAIN UPDATE[/COLOR]**-


How can I fix these not correctly mounted partitions?

There is clearly a problem here.

[IMG]http://s2.postimg.org/690dxy3h5/Screenshot_from_2015_07_06_00_04_42.png[/IMG]

---

### Post by bab1 on 2015-07-06
> **KurtisOmega said:**
> -**[COLOR=#ff0000]QUICK BUMP/MAIN UPDATE[/COLOR]**-


How can I fix these not correctly mounted partitions?

There is clearly a problem here.

[IMG]http://s2.postimg.org/690dxy3h5/Screenshot_from_2015_07_06_00_04_42.png[/IMG]
You are going to be better off showing terminal information my posting it between [noparse]```
 
```[/noparse] code blocks.  Just click on the [SIZE=5]**# **[/SIZE] icon and past the contents between the blocks.


The terminal output you do show indicates that you used an incorrectly formatted command (chown) and you used an inappropriate command (fdisk) as indicated by ```
WARNING:GPT ...
``` 

If you want to align the partition boundaries you need to use gparted when running Ubuntu from the LIVE version.  Several people have mentioned this in previous posts.  What do you want to do?  Why not take their advice.

[COLOR="#0000FF"]Edit:  The partitions are not *mounted incorrectly*, they sized (starting and ending) incorrectly to fit in the HHD formatting boundaries.[/COLOR]

---

### Post by oldfred on 2015-07-06
The entry in the protective MBR that gpt has, is just so old tools like fdisk do not see empty drive and try to partition it. It does not have any real use in gpt, so any errors from it do not really matter.

Gpt partitions should start at sector 2048 which all new partition tools use.
If drive was only MBR(msdos) then it also should start at 2048, so that is probably why fdisk is giving sector error.

---


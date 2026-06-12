---
title: "Raid problem on 7,04"
date: 2007-07-02
forum: General Help
---

### Post by J.One on 2007-07-02
Hi to all! I have a pentium 4 @ 2500 with 3 hard drives (ide) wich one of those is on raid controler and it has only storage files.The other 2 has ubuntu feisty and the other one windows.I don't use dual boot, but i switch each time from Bios to master, on wich platform i want. The matter is that from windows i can see all 3 drives and from ubuntu i can't see my storage drive on Places>Computer but i can see it from hardware information.I also have download some raid tools from synaptic package manager but no solution.Any ideas? Thnx...

"No mount problems, it just cannot see my 3rd drive"

---

### Post by khedron on 2007-07-02
Is the drive mounted in /media ? I think the Places menu only sees folders in /media/.

---

### Post by Kosmi4 on 2007-07-02
i have the same problem with my hard disks.
2 hard disks are connected at IDE1..The 1st is the master (Ubuntu 7.04) & the 2nd slave (Windows XP). I usually boot from HDD0 which has Ubuntu and when i want to boot from Win XP i change the boot order to HDD1 (XP) from Bios. I can see the Win XP HDD from Ubuntu and write on it with no problems. 
The problem is that i have connected one more HDD at the IDE RAID and i can't  see it from Ubuntu but i can with Win XP. This 3rd HDD is my data bank and i want to use it.  
I installed some packages from Synaptic Package Manager that had RAID tools but i still can't see it. It isn't shown even at hardware information..
Any help..? looking forward..
Thnx to all

---

### Post by reckless2k2 on 2007-07-02
have you both checked whether ubuntu supported your raid device? i had hardware raid that would not work with linux period.

---

### Post by J.One on 2007-07-02
Yes but how i can check if feisty supports raid?

---

### Post by Kosmi4 on 2007-07-04
I have tried to configure raid from the bios setup utility main menu.
I changed raid mode to normal (it was Stripe) but nothing changed and i still can't see the HDD  from Ubuntu. I want some help here plz.. i can't accept that XP can do something that Ubuntu can not... i have read a lot of forums but haven't find any help.
I probably miss something.. ?

---

### Post by Kosmi4 on 2007-08-03
bump

---

### Post by wcj786 on 2007-08-03
You can open a Terminal and type:

**fdisk -l** 

to find whether Ubuntu can see the drive, then, if it can, type:

**sudo mount  -t   /dev/drive_you_want_to_mount   /media/drive_name**

where the **drive_you_want_to_mount **is the drive name found using the **fdisk -l** command and the **drive_name **is the name you want to give to the drive under /media.

I found that I had to add the drive_name first, before using the **sudo mount** command.  Then, I could mount the drive.

I have an external USB RAID device and that is how I was able to get the device to function.  I still do not have it automatically mounting, but at least I can manually mount it and use the device.

P.S. If the drive is NTFS, you will need to get the packages for ntfs-3g and install them in order to write to the drive.

---

### Post by fjgaude on 2007-08-03
> **Kosmi4 said:**
> I have tried to configure raid from the bios setup utility main menu.
I changed raid mode to normal (it was Stripe) but nothing changed and i still can't see the HDD  from Ubuntu. I want some help here plz.. i can't accept that XP can do something that Ubuntu can not... i have read a lot of forums but haven't find any help.
I probably miss something.. ?

Look, you have to have a raid controller that has a Linux driver or you have to use software raid. You can tell if your Ubuntu version supports software raid by whether you have a man page for md. Try at a terminal: man md and see what happens. Kernel 2.6.20-16 supports up to raid 5.

If a page shows up then try man mdadm. mdadm is how you administer raid under Linux. It has everything one needs to handle raid 0, 1, 4, 5, 6, 10, Linear, and JBOD.

Now there is a way to us BIOS fakeraid using dmraid. Try man dmraid. And then google a how-to use dmraid with Linux.

Now if none of these show, simple install them with Synaptic or apt-get. They are supported by Ubuntu. E.g., sudo apt-get install mdadm dmraid.

frank

---

### Post by fjgaude on 2007-08-03
> **wcj786 said:**
> I have an external USB RAID device and that is how I was able to get the device to function.  I still do not have it automatically mounting, but at least I can manually mount it and use the device.


Would not an addition to your /etc/fstab file do the job. Add a line like this at the bottom:

/dev/<raid device name>      /media/<raid>      ext3    defaults   0   0

That's what I do for my software raid array. Now if your filesystem type isn't ext3 put it in instead, e.g., ntfs.

frank

---

### Post by Kosmi4 on 2007-08-05
First of all thank you for your replies..
I typed fdisk -l  at the terminal but nothing happened. Then typed man mdadm and saw the options but didn't find any help there..What else should i try? 
I can't see my HDD yet.. :(

---

### Post by fjgaude on 2007-08-05
Did you type sudo fdisk -l? You need to be root for fdisk to show anything.

Did you type mounting the dev as suggested?

frank

---

### Post by Kosmi4 on 2007-08-06
OK my mistake.. so I typed sudo fdisk -l and found my 2 HDD's at IDE 1 but not my 3rd on RAID.. This is what i get:


Disk /dev/sda: 61.4 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7163    57536766   83  Linux
/dev/sda2            7164        7474     2498107+   5  Extended
/dev/sda5            7164        7474     2498076   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        9729    57665317+   7  HPFS/NTFS


What i have to type to mount the missing HDD?

---

### Post by fjgaude on 2007-08-06
Since the raid device doesn't show with fdisk -l I can't say yet what to do to mount it.

Tell us, how is your raid setup? Is it a separate external device? Is it running off your motherboard raid controller? Is it what is called fakeraid? Was it generated using dmraid or mdadm?

Knowing this we might be able to mount the device.

frank

---

### Post by Kosmi4 on 2007-08-07
Well this HDD has my Private Files only (no operating system, NTFS format), and it is plugged at the green IDE slot of the motherboard. (i have the P4 Titan 8SQ800 Ultra AGP8X/Dual Channel DDR motherboard from GIGABYTE).This motherboard has 2 IDE slots and 2 green IDE slots named IDE RAID: ITE GigaRAID IDE 0, 1, 0+1, JBOD function plus UDMA ATA 133 support.
Pressing ''Ctrl-F'' i enter the BIOS utility Main Menu. A screen appears with 5 options. [1] Auto configuration, [2] Define RAID, [3] Delete RAID, [4] Rebuild RAID, [5] RAID card configuration.I click the first field to set an array, and at the Setup Array Type as: i give Normal (the only acceptable value.. other values like RAID 0, 1, 0+1, JBOD give me this error: Two hard drives have to be attached). I press ''Ctrl-Y'' and i save my changes. Then at the next menu [2] Define RAID, a list showing 5 columms (Array No, Array mode, Drive No, Size(MB), and status), with 4 rows (Array 0, Array 1, Array2 and Array 3), is empty. The user manual says that when an array is not  assigned a RAID level, you will see''- - - - - - '' on the row. (that is what i get). But i can't understand why at the Define RAID Sub-Menu in a box named Drive Assignments i can see my HDD (name and size). Note that in the same page at the status columm says ''Not Functional''... How can i see this HDD from Windows and i can't from Ubuntu if it is not functional? (If this helps, i have installed the ITE IT8212 ATA RAID Controller driver from the motherboard CD, at Windows).
I am so confused.. do you believe we can make it work? 
Thanks for your help so far.. I really appreciate it.

---

### Post by fjgaude on 2007-08-07
Okay, I'm getting there. Do a Google search for your ITE board and see just what others have gone through to make it work with Linux, going back over five years or so.

I assume you have at least two drives in the raid array? Is it raid1 or raid0?

If you are lucky you can download the Linux faderaid package and see if your ITE shows:

sudo apt-get install dmraid

After installed do a sudo dmraid -tay

and see if you find something like:

sil_ahahbjagbcag: 0 586070830 linear /dev/sdb 0
sil_ahahbjagbcdc: 0 586070830 linear /dev/sdc 0
sil_ahahbjagbcei: 0 586070830 linear /dev/sdd 0
ERROR: opening "/dev/.static/dev/mapper/sil_ahahbjagbcag"
ERROR: opening "/dev/.static/dev/mapper/sil_ahahbjagbcdc"
ERROR: opening "/dev/.static/dev/mapper/sil_ahahbjagbcei"

If you do you can mount /dev/mapper/ite_abcdefghijkl to a mountpoint on your OS drive, like /mnt/raid.

The last part is the name of your device in Linux.

Let us know what happens. If dmraid doesn't work you will have to educate yourself on what it takes to compile a ITE driver for Linux to get the board and its drives vision under Ubuntu.

Good luck.

frank

---

### Post by Kosmi4 on 2007-08-07
First I found & downloaded from a Bulgarian site an .exe file named driver raid ite 8212 linux. I installed it to my system but nothing changed...(note that from System/Hardware Information, i see now: IT/ITE 8212 Dual channel ATA RAID controler (PCI version seems to be 8212, embedded seems to be 8212), if it means something). 
Then i typed "sudo dmraid -tay" at the terminal and i got "No RAID disks". I don't known if it matters but the hard disk i want to mount is a Maxtor 4D060H3 simple HDD (no SATA or SCSI).
The only info from Google search i got, is that Gigabyte.com.tw has no Linux drivers at all, and others with the same problem still can't use their HDD's..
I believe the only solution i have is to boot from Windows, go to the HDD where are my files, and copy them to the HDD i use with Ubuntu.... 
I can't think something better.. :(  
Thank you for everything

---

### Post by fjgaude on 2007-08-07
Okay, case closed... happy computering...

frank

---


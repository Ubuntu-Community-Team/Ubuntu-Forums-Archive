---
title: "New SATA Seagate 2TB - Bios sees it - Ubuntu doesn't"
date: 2012-12-30
forum: General Help
---

### Post by held7over on 2012-12-30
Ubutnu 12.04
HP M8000N 64 bit dual AMD core  SATA 1 and 2 capable with 4 SATA sockets
New Seagate Barracuda 2TB ST2000DM001 Hardrive - auto-negotiate capable of SATA 1, 2, or 3

I have two SATA 1 hardrives LVM-ed together as my primary Drive. I want to use the new Seagate Barracuda as a backup drive for the LVM-ed drive until I can purchase a second 2TB drive to replace the LVM setup.

The Bios sees the New Seagate drive, but Navigator and System Monitor do not. Nor does the Ubuntu LiveCD installer, so, I haven't been able to partition, format and install an operating system on the New drive.

I haven't yet tried jumpering the New Seagate to force a SATA level. It is suppose to choose it's own SATA level automatically, and I am thinking that since the BIOS sees it and the BIOS can order the Self Checks I has picked a usable SATA level. Am I wrong?

**Stupid Question:** Do all the drives have to be the same SATA level? My LVM-ed drives are SATA 1, but the bios is set for SATA 1+2.

The Bios SMART Status Check - PASSED
The Bios SMART Short Self-Test - PASSED  0 errors
The Bios SMART Extended Self-Test - PASSED 0 errors

**In Bios Main I see:**
1st Drive------[None]
2nd Drive------[None]
3rd Drive------[WDC  WD6400AAKS] <---First LVM-ed Drive
4th Drive------[ATAPI  DVD A]<-------My DVDrom
5th Drive------[ST3500630AS]<--------Second LVM-ed Drive
6th Drive------[ST2000DM001-1C]<-----My New Seagate Drive

**In Adavanced I see:**
PATA Controller------[Disabled] <-Everything is SATA (4 SATA sockets)
SATA Controller------[Enabled]

**In Boot I see:**
Boot Device Priority:
HDD Group Priority [WDC WD6400AAK]<---My 1st LVM-ed Drive

Thanks for your suggestions and thoughts! :p

---

### Post by Slaygod on 2012-12-30
Kinda a dumb, common-knowledge question, but what capacities are your other drives? If I remember right, BIOS can only see 3TB or so, more and you need UEFI. Correct me if I'm wrong, I sometimes have these facts wrong. ;)

---

### Post by held7over on 2012-12-30
For me, it wasn't common knowledge. I had asked the advice of a Linux guy with lots more experienced than I have, who does run large drives in his servers, and he had told me to just drop it in and it should work just fine out of the box with my setup. No mention of a Bios total size limit. 

Actually, I had installed the 2TB hard drive in a different computer all by itself to start with, figuring to begin by backing up across my network until I had acquired a second 2TB hard drive to replace the LVM drives, but that system's Bios didn't see the 2TB hard drive at all and Linux couldn't see it either! So, when I moved the 2TB drive to my primary system with LVM drives, I was happy to see the Bios saw it, but since Linux wasn't seeing it....I figured this was some continuation of the same problem on the other computer...

After reading your comment, I simply disconnected the LVM's and was immediately able to partition the drive, and in doing so, I left enough free space on the drive so that the drive was effectively smaller than 2TB since my LVM drives totaled 1.1 TB. Everything works! Thanks!

Now I just have to figure out if it is possible for me to change the BIOS to the UEFI firmware you mentioned....whatever that is!

Thanks again! :P

---

### Post by Bashing-om on 2012-12-30
held7over; Hi !

These links may shed a bit of light on this dark situation of large disks:
[http://www.expertslogin.com/linux-administration/guid-partition-table-in-linux-partition-large-size-disk/](http://www.expertslogin.com/linux-administration/guid-partition-table-in-linux-partition-large-size-disk/)
[http://ubuntuforums.org/showthread.php?p=12254717#post12254717](http://ubuntuforums.org/showthread.php?p=12254717#post12254717)
follow the links in post #19 in particular.

[INDENT][INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dcstar on 2012-12-31
> **held7over said:**
> 
.......
Everything works! Thanks!


Then MARK the thread!

---

### Post by held7over on 2012-12-31
Bashing-om - Thanks for the URLs! I will check them out! :p

---

### Post by oldfred on 2012-12-31
UEFI is the new replacement for BIOS. UEFI normally uses gpt partitioned drives. Windows only boots from gpt drives with UEFI. 
But Ubuntu will boot from gpt partitioned drives whether UEFI or BIOS. I have BIOS, not UEFI.  I use gpt on a 160GB drive, my 64GB SSD and even on one flash drive just to see if it would work.

MBR(msdos) partitioned drives have a max of 2TB, so you do not have to convert to gpt unless you want to. Default installs of Ubuntu on empty drives somewhere over 1TB will use gpt.

To see your LVM from a new desktop install, you will  have to add the lvm2 driver.

sudo apt-get install lvm2

---

### Post by held7over on 2012-12-31
Thanks Oldfred! 

Evidently I did get one thing right, I already am using the lvm2 driver.

It's bothering me why the first computer's (Compaq HP sr1303wm) BIOS which originally had a SATA 640 GB drive in it, wouldn't show the SATA 2TB drive in it, when it was the only hard drive I had in that computer? Am I looking at an additional limitation do you think or does this sound like I just messed up and didn't work witht he BIOS long enough in that older machine?

---

### Post by oldfred on 2012-12-31
Was older machine in IDE mode?

With SATA you should have AHCI, or at least LBA or large, but not IDE. I think my SATA drives worked with LBA, but with my now 1 year old SSD, I had to change to AHCI for trim to work, but then XP did not work which was a plus as I had said I was going to stop using XP.  :)

---

### Post by held7over on 2012-12-31
Yes! It was in IDE Mode. 

I remember I had physically pulled the IDE connectors and the power connectors for those IDE drives that were in it, when I connected up the SATA drive. I was thinking I had just outsmarted the machine....(sick!)

The BIOS in that older machine didn't show a SATA option at all. It only had in the ADVANCED AREA:

Local Bus IDE Adapter

--and your choices are:

Disabled
Primary
Secondary
Both

I bet I should have DISABLED the Local Bus IDE option, but instead, the "BOTH" option was left enabled. 

I was thinking that at one time I had both SATA and IDE drives in it at the same time, but now I am thinking I had tried that a long time ago but it would only work with one type at a time. Maybe I am wrong about that, but I can see some more hardware experimenting in my future on this. Ha! If I could get a second 2TB drive to work as a backup on my network in this old machine, that would be just fine with me for now.

---

### Post by oldfred on 2012-12-31
That looks like a newer BIOS that supported IDE with cable select capability. But you have to use the 80 conductor cable. Otherwise with 40 conductor cable you have to set master & slave on hard drive with the jumpers.

---


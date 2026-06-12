---
title: "&quot;GPT detected. Please create a BIOS-Boot partition.. ??"
date: 2020-12-13
forum: General Help
---

### Post by ra7411 on 2020-12-13
I've run into some problems doing an install. This is a Ryzen machine running on an MSI 450 mobo. 
The machine has sda1 as /,   sda2 as /home, and that runs fine. 

 Sdb is mainly a backup hd and I put sdb1 in for installing an auxillary ubuntu install.

The sdb1 install attempts have resulted in various problems,  and when I run boot repair I usually get:

"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."

I'm totally in the dark as to what where and how this "BIOS-Boot partition" should be done. On sda?, sdb? Anywhere on the already partitioned drives or at the end of an existing partition?  I haven't noticed a  "bios_grub flag" in gparted.

Some info would be great assuming this is a worthwhile step to take in the first place.

Thanks

---

### Post by CelticWarrior on 2020-12-13
That error suggests you booted the live session from which you tied to run Boot Repair in Legacy mode.
AMD Ryzen hardware should be installed in UEFI-GPT mode, no exceptions.

---

### Post by Dennis N on 2020-12-13
A bios_grub partition is needed when you install in BIOS mode on a GPT partitioned disk. See the attached screenshot. It has to have the bios_grub flag set. It should be (of course) on the GPT partitioned drive, usually first, but probably could be added elsewhere. It is left unformatted.

---

### Post by CelticWarrior on 2020-12-13
All the above is accurate but I must stress again that you don't want to do that - create a partition in order to do a "BIOS"/Legacy installation in a GPT drive -, you want to install in UEFI mode!...

---

### Post by ra7411 on 2020-12-14
I think I've got this fixed. Maybe this description will help others. Lots of grub and install problems as described in my op post.

I changed my 500g ssd to gpt (from mbr). My 4tb hd was already gpt. On my previous 18.04 re-install attempts I had been getting failures and web pages showing this being reported as a bug by a lot of people and they were working on it as a bug.

On the mobo I tried both "uefi" and "uefi +legacy" - neither worked.

My 18.04 install usb was over a year old and I decided to do it over and see if things would work better. The install failed but the problem messages were way more helpful and plainly told me to put in a 35 meg efi partition - I put one into sdb and still got a failed install, then added one to sda and that was it - it installed normally, with the mobo set to "uefi +legacy". 

All this after having 10 months of no problem installs and re-installs with one disk mbr and the other gpt. I've seen people mention mbr and uefi but, needing a 35 meg efi partition is way new to me, most of the install failures didn't mention it and the boot-repair ususally talked about a "[COLOR=#000000]>1MB, unformatted filesystem, bios_grub flag".[/COLOR] 

You learn something new every day :D

---

### Post by oldfred on 2020-12-15
Your 35MB is not very large.
Windows used to use 100MB, we normally suggest 300 to 500 MB. 
I only use a small ESP of 100MB when installing a full system to my USB flash drives where I normally only install some software & will not use system a lot. 

My new Kubuntu install is only using 16MB in the ESP. But I may use it to download & update UEFI as UEFI can only read from FAT32 partitions. Some users use SystemD boot instead & that puts a lot of the files normally in /boot into ESP.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

For grub to install to gpt(GUID) partitions you need an ESP - efi system partition formatted FAT32 with boto/esp flags. If installing in now 40 year old BIOS boot mode, you need a 1 or 2MB unformatted partition with the bios_grub flag. 

Do not use MBR(msdos) partitioning unless you must have Windows in old BIOS boot mode. Usually systems before Windows 8 as Microsoft required UEFI/gpt with Windows 8 release in 2012.

---

### Post by yancek on 2020-12-15
> I haven't noticed a  "bios_grub flag" in gparted 

It's there, after creating the bios_grub partition explained above, click it in the main GParted window to highlight it, then click on the Partition tab at the top and mouse down to Manage Flags and bios_gub is there.  Using EFI on a GPT drive is a lot better solution.

---

### Post by ra7411 on 2020-12-15
> **oldfred said:**
> Your 35MB is not very large.
Windows used to use 100MB, we normally suggest 300 to 500 MB. 
I only use a small ESP of 100MB when installing a full system to my USB flash drives where I normally only install some software & will not use system a lot. 

My new Kubuntu install is only using 16MB in the ESP. But I may use it to download & update UEFI as UEFI can only read from FAT32 partitions. Some users use SystemD boot instead & that puts a lot of the files normally in /boot into ESP.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

For grub to install to gpt(GUID) partitions you need an ESP - efi system partition formatted FAT32 with boto/esp flags. If installing in now 40 year old BIOS boot mode, you need a 1 or 2MB unformatted partition with the bios_grub flag. 

Do not use MBR(msdos) partitioning unless you must have Windows in old BIOS boot mode. Usually systems before Windows 8 as Microsoft required UEFI/gpt with Windows 8 release in 2012.

My sda efi is using 10 megs of 42; sdb efi is using 6 megs of 42.

I think it's odd the system worked fine and took occasional installs  re-installs fine for 10 months w/ no efi partitions, then this time consuming problem came up.

During an install, Ub 18.04 installer could see the drives, mbr or gpt, and in my case the lack of efi partitions. I was a long way into the process before my more recent 18.04 installer gave me an explicit message re. the efi partition that solved things.

I was using "something else" during the install attempts, do the other methods do automatic efi partition installs? 
Many people running into this might just quit.

---

### Post by oldfred on 2020-12-15
If you boot installer in BIOS mode, it automatically creates a bios_grub if it sees the drive is gpt.
If you boot installer in UEFI mode, it automatically creates an ESP - efi system partition.
Windows requires gpt with UEFI installs, UEFI highly recommends gpt, but Ubuntu will let you install in UEFI boot mode to a MBR partitioned drive, and probably should not.

Have not totally followed details of BIOS installs, but I understand Ubiquity now creates an ESP even with a BIOS install. I think that is a good thing if drive is gpt as user may later want to convert to UEFI, since most systems are now UEFI. But those with old BIOS only systems did not seem happy.

I started using gpt with a bios_grub in 2010 on my BIOS only system. And every new or repartitioned drive was then gpt, including larger flash drives. My only MBR drive was my old Windows XP as it required MBR. But in 2012, I not only added bios_grub but started adding an ESP to repartitioned drives, so I could in future use UEFI. But it was another couple of years before I had an UEFI system.

---


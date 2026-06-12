---
title: "Having issues using ubuntu on new SSD"
date: 2020-05-07
forum: General Help
---

### Post by iamtheeggman2 on 2020-05-07
Hi,

I bought a new SSD and I created msdos partition table, created ext4 partition, copied over the existing partition from linux 20:04 on a normal HDD, did a file system check on new system, it was ok, created a new UUID for it, copied that into the fstab file on the new SSD and hashed out the original filesystem for the HDD and then used grub customiser to update the grub on the old HDD to show the new system on the new sdb1 which is the partition on the new SSD however it only boots up linux on the original HDD despite also changing the disk order in the bios which I personally didn't think I needed to do since grub lets you choose which drive to boot. What have I missed here? Thanks in advance.

---

### Post by GhX6GZMB on 2020-05-07
I think you forgot the OS part. Just copying the partition does not make a new bootable disk, despite all the other things you've done.

---

### Post by CelticWarrior on 2020-05-07
I don't know yet what you're missing but let me tell what I'm missing or, even better, what I don't understand.
What are you trying to do? Cloning and existent OS, only a partition or...? What's the point, your end goal with this?
UEFI or BIOS? And segwaying from this, why "msdos"?
And no, Grub doesn't let you choose drives, it boots different OSes that may or may not be installed in different drives. BIOS/UEFI, i.e., the embedded firmware that starts the boot process let you choose different boot orders in the same or different drives but where it boots from first and which OS is then chainloaded is independent from the location of the bootloader.

---

### Post by iamtheeggman2 on 2020-05-07
> **CelticWarrior said:**
> I don't know yet what you're missing but let me tell what I'm missing or, even better, what I don't understand.
What are you trying to do? Cloning and existent OS, only a partition or...? What's the point, your end goal with this?
UEFI or BIOS? And segwaying from this, why "msdos"?
And no, Grub doesn't let you choose drives, it boots different OSes that may or may not be installed in different drives. BIOS/UEFI, i.e., the embedded firmware that starts the boot process let you choose different boot orders in the same or different drives but where it boots from first and which OS is then chainloaded is independent from the location of the bootloader.

Cloning the original OS partition so I used my computer on the new SSD.

"msdos" because it was an option forced on me in gparted, this a new function from I can see, I never once in 10 years got asked by a partition manager in linux to install a table before creating a ext4 partition, I presume it was all done on the fly and they changed this in 20.04.

I have another boot loader live cd installer on a disk somewhere I'll dig it out and see what happens.

---

### Post by HermanAB on 2020-05-07
I got to ask: Why?

It is so much easier to install the latest and greatest version, rather than copying an old and tired version.

---

### Post by iamtheeggman2 on 2020-05-07
> **HermanAB said:**
> I got to ask: Why?

It is so much easier to install the latest and greatest version, rather than copying an old and tired version.

I did say in my post I am using 20.04, I installed it the other week when it came out... I am just trying to avoid pratting about installing it again but I have yet again wasted way more time trying to do things properly than prat about installing it all over again. 

Well the only grub loader I found in my backup cds doesn't recognise the file systems on my computer which is strange. I think from my memory I used a program I downloaded but now cant remember what it is, it was a very easy to use grub installer. it let you choose which partitions and which mbr on the disks you had to install it to. Any suggestions?

---

### Post by CelticWarrior on 2020-05-07
> **HermanAB said:**
> I got to ask: Why?

It is so much easier to install the latest and greatest version, rather than copying an old and tired version.

+100

It always baffled by this. The OP likely spent twice the time already and for null results.


> "msdos" because it was an option forced on me in gparted, this a new  function from I can see, I never once in 10 years got asked by a  partition manager in linux to install a table before creating a ext4  partition, I presume it was all done on the fly and they changed this in  20.04.


No, the option wasn't forced. It was presented in a dropdown menu with lots of other options.
And if you never seen this before is because you never dealt with a blank drive before. Please note that a blank drive is new, never used, drive. A drive without partitions may already have a partition table. You can create a new one, the same type or different in Gparted, Device menu > New partition table... But if it already has one it'll allow you to create/delete/resize/move any partition without ever mentioning the partition table.

---

### Post by iamtheeggman2 on 2020-05-07
You see why does this recognise the second set of grub options are on the new disk sdb but doesnt actually boot it?

---

### Post by CelticWarrior on 2020-05-07
> **iamtheeggman2 said:**
> Well the only grub loader I found in my backup cds doesn't recognise the file systems on my computer which is strange. I think from my memory I used a program I downloaded but now cant remember what it is, it was a very easy to use grub installer. it let you choose which partitions and which mbr on the disks you had to install it to. Any suggestions?

If it's a new computer (~10 years or newer) it has UEFI, not BIOS. And UEFI wants installations in UEFI mode in GPT drives, not MBR ("msdos").
It seems you're set in the old ways (now called "Legacy/CSM/"BIOS") because you talk of partitions, MBRs, etc. It's strongly recommended that you learn about UEFI/GPT.
Start here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Then learn why you want GPT instead of MBR: [https://www.diskpart.com/gpt-mbr/mbr-vs-gpt-1004.html](https://www.diskpart.com/gpt-mbr/mbr-vs-gpt-1004.html)

---

### Post by CelticWarrior on 2020-05-07
> **iamtheeggman2 said:**
> Well I can only assume then the likes of Western Digital are handing out blank drives with an actual table on it with a partition then... 

Your assumption is correct. It applies to any new internal drive sold by any brand. External USB drives as well as USB stick are sold already formatted, internal drives never are. When you use one brand new drive to install an OS, no matter which one, the installer takes care of everything which includes creating, in this order, the partition table and all the partitions required for such instalation and that's why most users never became aware of the fact that drives have a partition table and/or that there are different partitions tables one can use depending on the circumstances.

> Clearly you have not read my original post either, I did state I was  copying over 20.04. MY mother said if you cant say anything  constructive...

At this point I must remind you that you're the one asking for help.
It is then constructive pointing out what you did wrong like we just did and also point you in the right direction, the things you need to learn to better achieve your goals and make use of your resources.

---

### Post by oldfred on 2020-05-07
Once you understand MBR & gpt, you will know you cannot just copy a gpt partition.
Gpt has many improvements over the 35 year old MBR. One of them is primary partition table with GUID, backup partition table with GUID, and each gpt partition has a GUID. If those get out of sync then you have major issues. 
You just cannot copy one gpt partition to another drive without corrupting drive with mismatched GUIDs.
And you just do not want to copy a gpt partition to a MBR partitioned drive.

Also any image copy retains UUIDs & GUIDs in partitions. And when rebooting you cannot have duplicates. 

Microsoft has required vendors to install in UEFI/gpt mode since Windows 8 released in 
2012. Apple Mac have used EFI/gpt since they converted to Intel chips long before that.
Only most systems that were Windows 7 or before (all now End of Life) used BIOS/MBR. And later versions of Windows 7 could be UEFI/gpt.

My last install was to a SSD that was blank, but then I partitioned in advance. And had ISO downloaded. Install then took about 10 minutes. Updates/reconfigurations then took less than an hour total.

---


---
title: "How to install Ubuntu and keep Vista"
date: 2007-02-13
forum: General Help
---

### Post by omBRE on 2007-02-13
Hi, I got laptop from my company and it has Vista installed. I hate Vista but I have to keep it because it is company's computer ann one day I will have to return it in same condition they gave me.
On that laptop I have one 160GB NTFS partition. I read that I am not supposed resize and make new partitions with Ubuntu partition manager, so I went to Vista's Disk Management and split that one 160GB NTFS partition into:

C: 76GB NTFS (System, Boot, Primary Partition)
G: 39GB RAW (Primary Partition) (aimed to be FAT32 to communicate between MS & Linux)
H: 24GB RAW (Logical Drive)       (aimed to be Ubuntu partition)
I:   4GB RAW (Logical Drive)       (aimed to be Ubuntu Swap)

Can someone please tell me if this partitions are made right? Can I start Ubuntu instalation? If this is desktop I would already try that, but since this is company's laptop I am affraid of doing that.:confused: 

Thanks

---

### Post by chris.snafu on 2007-02-13
looks proper, but are you sure you want 4 gigs for swap? you only need around 2 at the max... someone correct me if im wrong.

---

### Post by lamalex on 2007-02-13
4 gigs might be a lot for swap but you're not going to notice a hit by having it. they say the rule is double your memory, I have 2 gigs of memory, I dont use that, let alone another 4. you're good to go, youre just going to have a lot of swap headroom. bummer about visita. if i was your IT department, which i could be ([www.myremoteitdepartment.com]("http://www.myremoteitdepartment.com")) *eybrow eyebrow*, i would not be upgrading to vista just yet.

sorry for the shameless plug for where I work :lolflag:

---

### Post by omBRE on 2007-02-14
I have 2 gigs of RAM so I used that rule and made that 4 gigs partition. I know that is a lot, but I have 160GB of HDD and I want fill that. Problem is that we bought laptop with Vista on it. If it was XP I would live with it, but Vista I hate, it is making snail out of this fast computer...

---

### Post by Tuna-Fish on 2007-02-14
it's a good idea to have considerably more swap than ram on a laptop, even if it is not actually used, because that way you can suspend to disk.

---

### Post by bg1256 on 2007-02-14
Everything looks good!  One thing you may note is that a lot of people have had problems with GRUB when dual booting vista and Ubuntu.

There are several threads about it, though, so the problem should be a quick fix.

---

### Post by omBRE on 2007-02-14
Only thing that I am concern of is fact that Vista created Logical Drive for H: and I:, and not Primary partition as for G:. Can someone explain me what is difference between Primary Partition and Logical Drive? Can I install Ubuntu on H: if situation is like this:

C: 76GB NTFS (System, Boot, Primary Partition)
G: 39GB RAW (Primary Partition) (aimed to be FAT32 to communicate between MS & Linux)
H: 24GB RAW (Logical Drive) (aimed to be Ubuntu partition)
I: 4GB RAW (Logical Drive) (aimed to be Ubuntu Swap)

---

### Post by omBRE on 2007-02-21
Hi, it's me again.
Still no ubuntu for me.

I just started to install ubuntu, and on step 5 installer is showing me options:

Resize SCSI1(0,0,0), partition #3 (sda) and use free space
Erase entire disk: SCSI1 (0,0,0) (sda) - 160..0 GB ATA FUJITSU MHV2160B
Manually edit partition table

Why is it showing me that I have SCSI whem my disk is ATA
I chose option number 3 ( Manually...) because I don't wont to erase Vista and I don't wont ubuntu to deal with partitions - I heard that is not healty for Vista :)

After that it is showing me
01 /dev/sda-1 free Hidden 0.97MB
02 /dev/sda1  ntfs             6.36GB Recovery
03 /dev/sda2  ntfs Active   75.99GB
04 /dev/sda-1 free            6.73MB
05 /dev/sda3 unknow        26.54GB
06 /dev/sda-1 free             12.51GB
07 /dev/sda4 extended       27.64GB
+- 08 /dev/sda5 unknown 23.74GB
+- 09 /dev/sda6 unknown 3.90GB

I wanted to use this /dev/sda5 for ubuntu and /dev/sda6 for swap. Is it ok?
Once again it is companies laptop and I don't want to break it...

---


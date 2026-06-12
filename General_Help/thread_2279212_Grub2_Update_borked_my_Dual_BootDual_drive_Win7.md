---
title: "Grub2 Update borked my Dual Boot/Dual drive Win7"
date: 2015-05-21
forum: General Help
---

### Post by Finn61 on 2015-05-21
Hi folks,

Trying to muddle my way through a Grub2 boot problem but struggling so far. Been using Kubuntu for many years but this one has me stumped and I'm not entirely up on the latest UEFI booting. Here's what happened, hope you can help.

I have Kubuntu 14.04 LTS running on my 500GB Samsung HD (/dev/sdb) and I had not too long ago moved Win7 onto it's own Samsung 500GB SSD (/dev/sda). My BIOS boots from /dev/sdb and that's where it runs GRUB2, boot menu appears with both Kubuntu and Windows options. Both worked perfectly. Happy days.

The other day I ran an update on Kubuntu, vaguely noticed Grub2 was part of the swathe of updates (wish I had have paid more attention) and pulled the trigger. Well now I can still boot to Kubuntu but Windows won't boot from the Grub menu - can't find the boot manager message comes up when I try ('efi/Microsoft/Boot/bootmgfw.efi' not found).

My suspicion is that Grub2 update has written over on drive /dev/sda rather than /dev/sdb or that the grub menu entry for Win7 is not pointing to the drive the boot manager is really on.

I did a dump with Boot-repair here:
[http://paste.ubuntu.com/11242129/](http://paste.ubuntu.com/11242129/)

Any suggestions or tips greatly appreciated. If I figure it out I will post back here also.

Cheers,

Andrew

---

### Post by VMC on 2015-05-21
I don't know efi either, but one thing you can do, is when you see grub menu, type 'c' for grub prompt. Then type 'set' at the 'grub >' prompt. It should show you what partition you are using to boot grub.

Edit: Near the end of the 'set' output , look for prefix =, and root = . That will tell you what partition your using.
For example, mine is:
 prefix = (hd0,msdos6)/boot/grub
root = hd0,msdos6

---

### Post by yancek on 2015-05-21
The generally accepted practice when using UEFI to boot is to have an EFI partition (FAT32) near the beginning of the disk.  You have efi partitions on both hard drives and the efi files for both operating systems in both partitions.  I don't believe that is necessary.  You also have Grub code in the mbr of both disks which is usually a bad idea with UEFI.  You also have a BIOS boot partition pretty close to the end of the second drive (Kubuntu) which is used when using GPT partitions and NOT using UEFI.  If you are going to use a boot partition it should be near the beginning of the drive.  You don't need this partition with UEFI.  I also noticed the UUIDs for sda1 and sdb1 are identical which seems a bit odd to me.  I don't have any suggestions to resolve this as I don't use UEFI on my computers but I'm sure someone will come along with suggestions.

---

### Post by Finn61 on 2015-05-26
Thanks for the responses guys.

Yancek - yes you are right the partitions are a dogs breakfast. I suspect this might be what's throwing Grub and also the Windows repair disk. I used a Samsung clone utility when I bought the SSD to copy the windows partition to the new drive. I wonder of this is how I ended up with duplicate UUIDs.

I will clean up the partitions. Delete the Grub legacy boot partition and also delete one of the EFI System Partitions (ESP), rerun Grub update, rerun Windows repair and see what happens from there. I will report back.

---

### Post by Finn61 on 2015-05-26
Well that wasn't too painful. I used Gparted and deleted the old legacy grub partition (sdb4). I also deleted the extra EFI partition from that drive (sdb1). So now the Kubuntu drive only has the swap and root partitions (sdb5, sdb6).

I left sda alone. It has an EFI partition (sda1), ms reserved (sda2) and the windows NTFS partition (sda3).

I reran: sudo update-grub

Now there is a Grub menu entry for Windows on /dev/sda and it works perfectly. (so does the Kubuntu entry).

I can only think that the fact there was 2 EFi partitions with identical UUIDs was confusing either Grub when it built the entries or the Windows boot manager. Either way, this one is now solved.

Lesson learnt: Keep hard disk partitions clean and tidy. Watch out of duplicates after cloning drives or installing multiple OS'es.

---


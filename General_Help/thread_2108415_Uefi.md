---
title: "Uefi"
date: 2013-01-24
forum: General Help
---

### Post by dmallion on 2013-01-24
So I have UEFI available and I was just wondering if its really worth it to use it. I will be installing os anyways so should I just stick with MBR and the old way or use this UEFI/ GPT stuff? What are the advantages?

---

### Post by Bobhuber on 2013-01-24
> **dmallion said:**
> So I have UEFI available and I was just wondering if its really worth it to use it. I will be installing os anyways so should I just stick with MBR and the old way or use this UEFI/ GPT stuff? What are the advantages?
Unless your running windows or intend to install windows I would stick with MBR. Note that UEFI is the fuure and will be default before long. Right now its a headache (IMHO)

---

### Post by oldfred on 2013-01-24
UEFI also requires gpt partitions.

Windows will only boot from gpt partitions with UEFI. So you also have to decide if you want gpt partitions. Ubuntu will boot from gpt with either BIOS or UEFI.

You only have to have gpt partitions if you have a drive over 2TiB or about 2.2TB. But gpt is suggested for SSDs also, but not required.

Some UEFI's are implemented better than others, even though it is a standard and some installs work better at booting with UEFI than others. BIOS/MBR has been around for ages, or since first hard drive with a PC, so most bugs and issues have been worked out and it is well understood.

I assume my next computer will be UEFI and I was planning on building it last summer, but did not get it done. But I converted one old drive to gpt, and used gpt on a new SSD but in BIOS mode.

For upgrade-ability I created both the efi partition at the beginning of the drive and a bios_grub for BIOS boot. It can be difficult to add a partition at the beginning of a drive and the efi is not large at 200 or 300MB. Then I can move my SSD to my new build without having to totally reformat.

---

### Post by Double.J on 2013-01-24
Hi there!

Are you installing on mac or PC? 

Chances are that the UEFI is just referring to the firmware of the motherboard;  (the bios) 

Please correct me if I'm wrong, but I'm going to assume you are referring to drive partition tables?  For example when it says "write partition table" in gparted, it gives you the option to write MBR or GPT 

We're basically talking about how partitioning will work on your drive. MBR is the traditional partition table system that you've used for ever most likely. The rules are simple; you can have four "primary" partitions; where you can install things such as windows, Mac OS, bsd, etc. you can Also use one of those partitions as "extended" which can house many (up to a hundred or so) smaller partitions. Linux can boot and use logical partitions and will by default. 

Say you have windows installed and you ask ubuntu to install alongside. Windows uses two primary partitions from vista onwards. Your computer may also come with a recovery partition, making three primary partitions. That leaves only one slot on the drive. Ubuntu shrinks windows to make itself some room, then creates one extended partition. The drive is now full; there are four partitions. It can hold no more. Because the final partition was "extended", ubuntu is now able to make one partition for / and one for swap. That means that there is now a total of 5 partitions on the hard drive. All very clever.

However, what if in your love of Ubuntu, you decide to install ubuntu+1... Well that's okay because you can add more logical partitions. But what if your love of open source and unix means you want to try bsd? That can't use you're extended partition. Or maybe you want to also add windows 8 ... Windows has to have a primary, so now the drive is full.

Enter GPT, the replacement to MBR. There are no partition types now; just partitions, so you can install loads of different OS on your drive. It also has a benefit that is becoming more relevant; because we've had MBR forever, some things weren't planned for. One of these is maximum drive size.  If you want a drive bigger than 2.2TB you need GPT. Additionally GPT has redundancy built in. MBR has only one .. Err MBR? 

This is the master boot record. A tiny section right at he start of the hard drive that remembers where the partitions are and where the computer should be booted from. GPT has more than one, so if one becomes corrupted, the computer will still boot. Now I know you're thinking that you've never had a corrupted MBR. And it doesn't happen often, but mistakes do happen especially with the DD command!!  So all in all you can have lots of partitions, massive disks and if you accidentally write over your partition table it isn't game over. But there's more. Wih MBR if you move partitions around, it looses them and then it won't boot. Again GPT to the rescue - it remembers the partition, not the disk location so it will still find it if they swap places.

So why doesn't everyone use it?

Well it's still kind of new ish... So a few OS still don't support it;  they need an MBR sector on the disk. For the most part this is fine; you can create a tiny partition usually called a bios boot partition. This is basically creating a fake MBR one the GPT disk to fool the legacy OS. 

All in all, in my experience the only reason not to take advantage of GPT is that everything is designed for MBR, so initial install can be more complicated on some OS, or you don't want to wipe out the disk to change the partitioning type. It isn't quite as easy, but I think the rewards are worth it.

Just remember

ALWAYS BACK UP

CHANGING THE PARTITIONING REQUIRES YOU TO REINSTALL, consider it the same as ERASING your disk.

---


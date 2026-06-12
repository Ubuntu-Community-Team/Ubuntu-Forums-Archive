---
title: "Should the /home partition be primary or logical on a Master Boot Record HDD scheme?"
date: 2018-06-04
forum: General Help
---

### Post by John_Patrick_Mason on 2018-06-04
Two days ago, I decided to reinstall Lubuntu from scratch by manually creating the individual partitions instead of automatically having the partitions created for me using a live CD using [this]("https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") guide.
In one of the comments, a user known by the username LiveWireBT writes that HDDs that are still using the legacy BIOS firmware should set the root partition as primary rather than logical. The guide also seems to suggest setting the /home partition as logical.

Here are my questions:
1) When should I set a partition as primary instead of logical?
2) Was I supposed to set the /home partition as primary rather than logical given that I was using an HDD with BIOS firmware?
3) When should I set a partition's location at the beginning or end?
4) How big should the /home partition generally be if installing on a HDD with only one operating system?
5) What about creating separate partitions for /boot /var and /tmp? What are the advantages of creating these separate partitions? Again, should they be primary/logical, beginning/end?

Thanks in advance.

---

### Post by vanadium on 2018-06-04
> **John_Patrick_Mason said:**
> 
1) When should I set a partition as primary instead of logical?

Essentially does not matter. Logical partitions allow to have more than four partitions on one volume. If you need less than four, it practically does not matter whether you set up partitions as primary ones or as logical partitions in an extended partition,
> 
2) Was I supposed to set the /home partition as primary rather than logical given that I was using an HDD with BIOS firmware?

Not specifically.
> 
3) When should I set a partition's location at the beginning or end?

On traditional drives, access to the start of the drive is (theoretically mostly) faster than at the end. Usually, the system partition comes first. But again, does not matter really for practical purposes of desktop use.
> 
4) How big should the /home partition generally be if installing on a HDD with only one operating system?

Really as you wish. Depends on how you want to organize your data. Most practical for desktop use is probably to have /home allocate all available space after the system partition and eventually the swap partition.
> 
5) What about creating separate partitions for /boot /var and /tmp? What are the advantages of creating these separate partitions? Again, should they be primary/logical, beginning/end?

None, unless you are maintaining a server system, where splitting these directories in dedicated partitions, eventually on different drives, may have advantages for maintenance and minimizing down time.

Just my 5 cents, and from the perspective of typical desktop use. You will have to indicate your specific user case if it is different.
By the way, Linux boots equally fine from a primary as from an extended partition. So also there, it does not really matter for a desktop system (or laptop).

---

### Post by HermanAB on 2018-06-05
On Linux, the partition type doesn't matter.  You can install a Linux file system directly on a block device without making a partition.  On Windows, it used to and may still matter.

---

### Post by oldfred on 2018-06-05
If never installing Windows in BIOS boot mode to drive ( BIOS Windows requires MBR), I would suggest using the newer gpt partitioning. If BIOS booting you do need a small 1 or 2 MB unformatted partition with bios_grub flag for grub to correctly install.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by monkeybrain20122 on 2018-06-05
It doesn't matter. You need a logical partition for MMR only if you need more than 4 partitions (multiboot) If you just need a separate /home you can make 2 primary partitions. You need a relatively small / partition for the system (normally < 20G but you can make it bigger just in case especially if you plan on installing games since they are big) the /home should be big since it houses your data. 

optionally you can make a swap partition.

You don't need /boot unless you want to encrypt your drive or something, otherwise it is just headache if your old kernels pile up there and break your system (you can set autoremove to be automatic, but why bother, you don't need /boot)

Unless you need more than 4 primary partitions or (?) have a hdd > 2TB I don't see any advantage of gpt.

---

### Post by John_Patrick_Mason on 2018-06-05
[QUOTE=vanadium]Essentially does not matter. Logical partitions allow to have more than  four partitions on one volume. If you need less than four, it  practically does not matter whether you set up partitions as primary  ones or as logical partitions in an extended partition.[/QUOTE]

What do you mean by an extended partition? I'm not yet familiar with this term. 

[QUOTE=vanadium]On traditional drives, access to the start of the drive is  (theoretically mostly) faster than at the end. Usually, the system  partition comes first. But again, does not matter really for practical  purposes of desktop use.[/QUOTE]

What do you mean by traditional drives? You mean hard disk drives (HDDs) as opposed to solid-state drives (SSDs) irregardless of whether a hard drive has BIOS or UEFI firmware? Also, when deciding whether a partition should come at the beginning or end, if I set the system partition (/) to come at the beginning, and I then decide to create a separate /home partition, if I set the /home partition to also come at the beginning, will the /home partition override the root partition and come *before* the root partition, since I set the /home partition to come at the beginning, or can I set both partitions to come at the beginning without one overriding/interacting with the other?

[IMG]https://i.stack.imgur.com/f9AS5.png[/IMG]

[QUOTE=monkeybrain20122]It doesn't matter. You need a logical partition for MMR only if you  need more than 4 partitions (multiboot) If you just need a separate  /home you can make 2 primary partitions.[/QUOTE]

What is MMR? Do you mean MBR? Also, you mean 4 partitions as opposed to 4 volumes/operating systems, correct?

---

### Post by vanadium on 2018-06-05
The old MBR partitioning scheme allows only four primary partitions. There is a way to have more partitions. That involves substituting a primary partition for an extended partition. In such extended partition, an unlimited number of logical partitions can be created.

Otherwise put, if you have a logical partition, you will certainly also have an extended partition, because that is needed to host the logical partition.

Yes, with "traditional" drive I was referring to the magnetic drive. BIOS or UEFI is not firmware of the drive, though. You can only use space once, so you can place only one partition at the start of the drive. However, as I said before, I do not consider it to have practical relevance whether a system or a home comes first, and second, the theoretical relevance comes only with a classical magnetic drive.

---


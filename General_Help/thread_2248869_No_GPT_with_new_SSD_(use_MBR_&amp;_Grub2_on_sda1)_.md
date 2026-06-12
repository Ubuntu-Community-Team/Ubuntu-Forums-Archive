---
title: "No GPT with new SSD (use MBR &amp; Grub2 on sda1) w/ Xubuntu LTS &amp; Debian Stable. Is OK?"
date: 2014-10-17
forum: General Help
---

### Post by mikodo on 2014-10-17
I was reading an oldfred's response about GPT with SSD's [here.]("http://ubuntuforums.org/showthread.php?t=2248816") I want to install a SSD on my 2009 intel machine, that appears to not have a boot manager that can specify an EFI-mode boot to use GPT. I looked, and couldn't find one in the BIOS. (That is the right place to look, isn't it?).

I am quite happy with a MBR, with  grub2 on sda1 and forgetting about GPT, for Xubuntu LTS and Debian Stable. **Will that continue to work well enough, with a new SSD? **

Thank you.

---

### Post by yancek on 2014-10-17
I'm not sure what you are planning to do.  Are you going to install another operating system on the SSD?  If you just want to use the SSD as a data partition you don't need anything in the mbr of the SSD.

---

### Post by mikodo on 2014-10-17
> **yancek said:**
> I'm not sure what you are planning to do.  Are you going to install another operating system on the SSD?  If you just want to use the SSD as a data partition you don't need anything in the mbr of the SSD.

Thank you.

I apologize, for not giving more information. I also see that in the title "/"'s, is incorrect. I am going to edit the title to reflect, as below.

I plan to install, just Xubuntu LTS's and Debian Stable installs, on the SSD. With them, to use a new platter disk to have a symlinked "data partition". Nothing else on the machine.

---

### Post by mikodo on 2014-10-17
I can't use GPT, even if I had wanted to.

This excellently written guide, ["T]("http://www.rodsbooks.com/refind/bootmode.html")[he rEEDInd Boot Manager: What's Your Boot Mode?]("http://www.rodsbooks.com/refind/bootmode.html")["]("http://www.rodsbooks.com/refind/bootmode.html") by Roderick W. Smith and others he has available on-line, for explanations on this subject, provided me with the commands to show if a computer has "EFI, of which the GPT definition is a part".

I didn't find it in BIOS, because I don't have it.

 With this computer, I must continue to use the MBR with Grub2.

**I hope the SSD, will work well, without GPT.**

---

### Post by Dennis N on 2014-10-17
> With this computer, I must continue to use the MBR with Grub2

You don't need UEFI firmware to use a disk with a GPT partition table. The laptop I am using now is from 2007 with a traditional bios and I am using a GPT formatted HDD. All partitions are primary (no extended and logical partitions), and there are 128 primary partitions by default.

---

### Post by mikodo on 2014-10-17
> **Dennis N said:**
> You don't need UEFI firmware to use a disk with a GPT partition table. The laptop I am using now is from 2007 with a traditional bios and I am using a GPT formatted HDD. All partitions are primary (no extended and logical partitions), and there are 128 primary partitions by default.

Thank you,  Dennis.

Back to searching for me.

---

### Post by oldfred on 2014-10-17
This is also by Rod Smith when he was still in this forum.
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

I have been using gpt with my BIOS only computer since version 10.10 or Oct 2010.

You do not see any reference to gpt nor MBR(msdos) in BIOS or UEFI. BIOS or UEFI is how system boots. MBR or gpt is how drive is partitioned.

Windows only boots from gpt partitioned drives with UEFI.
Both Windows & Ubuntu only boot from MBR drives with BIOS.

And gpt spec was in coordination with UEFI, but Ubuntu will boot in BIOS or UEFI mode from a gpt partitioned drive.
      
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

But there is no requirement to use gpt, it was a suggestion.

---

### Post by mikodo on 2014-10-17
> **oldfred said:**
> This is also by Rod Smith when he was still in this forum.
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

I have been using gpt with my BIOS only computer since version 10.10 or Oct 2010.

You do not see any reference to gpt nor MBR(msdos) in BIOS or UEFI. BIOS or UEFI is how system boots. MBR or gpt is how drive is partitioned.

Windows only boots from gpt partitioned drives with UEFI.
Both Windows & Ubuntu only boot from MBR drives with BIOS.

And gpt spec was in coordination with UEFI, but Ubuntu will boot in BIOS or UEFI mode from a gpt partitioned drive.
      
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

But there is no requirement to use gpt, it was a suggestion.

Thank you, Fred. I did read, the links you provided. I see some advantages GPT brings over MBR, even for small drives. I think, why not. But, I also saw what Rod Smith wrote, about staying with MBR if one wishes to use it, and your statement of, *"there is no requirement to use gpt, it was a suggestion"*. Thank you, for the how to with gparted.

So, I will try "GPT". It's nice to learn useful things.

My best.

*Note to self, quoting oldfred from, [here.]("http://ubuntuforums.org/showthread.php?t=2248816") "*And with gpt booting in BIOS mode you need a tiny 1 or 2MB unformatted partition with the bios_grub flag.*"

---


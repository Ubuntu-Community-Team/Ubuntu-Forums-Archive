---
title: "gptsync"
date: 2014-07-12
forum: General Help
---

### Post by nadun3 on 2014-07-12
Hello I have a question about gptsync: i have made the following partitions: 
75GB Windows 8 Partition. ntfs
75GB Ubuntu partition. ext4.
75GB Backtrack partition. ext4.
and unallocated space
and then i did sudo apt-get install gptsync
and then i gptsync /dev/sda2 and made hybridmbr
and then I went and installed windows 8 and then backtrack and then Ubuntu and now I have a successful triple boot system using the grub bootloader and now I am wondering if I can make another partition with the unallocated space (plan to make another ntfs for windows 8.1) and then do gptsync again without stuffing up my current windows 8 stuff i.e. no loss of data?
Thanks

---

### Post by oldfred on 2014-07-12
Why a hybrid gpt/MBR?
Better to have all gpt if you can use UEFI or all MBR if not UEFI?
Windows only boots from gpt with UEFI.
Windows and Ubuntu only boot from MBR with BIOS.
Ubuntu will boot from gpt with either MBR or BIOS, but you can only use grub to boot systems installed in same boot mode.
I do not think with hybrid you can have more than 4 primary partitions in MBR and they must be the first 4.

 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---


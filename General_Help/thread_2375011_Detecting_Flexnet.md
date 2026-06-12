---
title: "Detecting Flexnet"
date: 2017-10-21
forum: General Help
---

### Post by mörgæs on 2017-10-21
How can I detect if Flexnet or similar software is present in the boot area of the hard disk? 

I'm aware that Grub now yields to this class of rogue programs and I am aware that I can erase the boot area in order to get rid of it but I would like to see what's hiding there before erasing.

---

### Post by oldfred on 2017-10-21
This is where grub-pc does the check, but it is C which I do not know and is checking for a variety of embedded code.

fred@Z170N:~/Downloads$ find . -type f -print | sed 's/ /\\ /g' | xargs grep -i "Flexnet"
./grub-2.02~rc2/grub-core/partmap/msdos.c:      .name = "FlexNet",
./grub-2.02~rc2/grub-core/partmap/msdos.c:      .name = "FlexNet",


I would first just check using hexdump or similar to scan first sectors of drive. Often Flexnet was in first few sectors like sector 32.
Old BIOS/MBR partitions started first partition at sector 63, but newer ones now use 2048.
 sudo dd if=/dev/sda bs=512 count=62 | hexdump -C 


With UEFI Windows uses the system reserved for the space to stuff that type of code. The gpt partitioning has no sectors after gpt's protective MBR, so other spaces are required. Grub adds bios_grub if installing in BIOS mode to gpt drive. Both Windows system reserved & Linux' bios_grub serve the same purpose as the space after the MBR, but now separate so no conflicts.

---

### Post by mörgæs on 2017-10-22
Thanks. As fas as I could see there was no trace of Flexnet in the dd output.

Will try some more computers when I get to them and post back.

---


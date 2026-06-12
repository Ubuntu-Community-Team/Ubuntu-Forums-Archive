---
title: "Grub menu is broken"
date: 2021-11-19
forum: General Help
---

### Post by pierre-bouard on 2021-11-19
Hello,

After a windows 10 update my ubuntu grub menu doesnt work

When i boot on my ubuntu disk, i have the minimal grub command.
Windows 10 is on her own disk.

I made a boot repair iso and this is the output :
[https://pastebin.ubuntu.com/p/nWtR9fHZkp/](https://pastebin.ubuntu.com/p/nWtR9fHZkp/)

Can you help me

---

### Post by yancek on 2021-11-19
For some reason, your boot repair output shows a lot less information than expected.  Your boot repair does not show any sign of Ubuntu other than the entries on sda2 which is the EFI partition.  You have the correct Ubuntu and windows EFI files and the only partition Ubuntu could be on is sda4. The only other drive showing is the Verbatim USB. 

Are you able to access your BIOS firmware to select to boot Ubuntu in that manner?
Could you check your BIOS to see if Secure Boot has been turned on as that some times causes problems?
Do you still have your Ubuntu install disk?  If so, I would suggest that you go to the boot repair site again and this time select the 2nd option described on that page using the ppa and again run boot repair with the Create BootInfo Summary option as I understand it is usually more up to date and may output more detailed information.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tea for one on 2021-11-19
[COLOR="#0000FF"]Line 63[/COLOR] - One OS Detected
[COLOR="#0000FF"]Line 65[/COLOR] - OS#1:   Windows 8 or 10 on sda4

No sign of Ubuntu in the report, although you have Ubuntu files in the EFI partition

[COLOR="#0000FF"]Line 87[/COLOR] - Boot0005* ubuntu	HD(2,GPT,4c67a212-c761-43d0-a5ef-9c5d568fa815,0xe1800,0x31800)/File(\EFI\UBUNTU\SHIMX64.EFI)
[COLOR="#0000FF"]Line 88[/COLOR] - Boot0009* ubuntu	HD(2,GPT,4c67a212-c761-43d0-a5ef-9c5d568fa815,0xe1800,0x31800)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO

If you have two disks, one with Windows and one with Ubuntu, then it looks like the Ubuntu disk was not accessible when you ran the report.

Can you boot either OS from your UEFI boot menu?
Can you check that both your disks are attached correctly?

---


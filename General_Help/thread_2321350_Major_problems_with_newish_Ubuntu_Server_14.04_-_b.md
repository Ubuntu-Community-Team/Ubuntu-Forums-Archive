---
title: "Major problems with newish Ubuntu Server 14.04 - black screen after Grub"
date: 2016-04-22
forum: General Help
---

### Post by eNRGy on 2016-04-22
Hi all,

I'm getting an instant black screen and no sign of further life immediately after Grub.

I installed Ubuntu Server 14.04 onto a Samsung 840 SSD with LVM and everything seemed to be fine. I set up my 4 2tb drives as a mdadm RAID array with LVM on top. I installed Kodi. I left the machine on for a few days while the RAID was set up and then copied my files on to it. Everything seemed fine. 

Then I try to reboot it. I get to the Grub screen. I choose "Ubuntu". Instant black screen with no further response. No response on ping or ssh either, no matter how long I wait.

Ctrl+Alt+Del reboots the system. I choose "Ubuntu (recovery mode)" and I get the following messages (Which may be a red herring):
"incrementally starting raid arrays
mdadm: Create user root not found
mdadm: create group disk not found
incrementally started raid arrays"
in a constant loop that goes on forever.

I have edited mdadm.conf to remove my RAID array, made sure it's not in fstab and disconnected the physical drives. RAID could be a red herring because mdadm errors can be to do with LVM I understand.

But could the black screen actually be caused by a graphics issue, maybe it's trying to start up in graphics mode because I installed Kodi? I'm uncertain what else gets installed with that but maybe the lack of Radeon drivers is the issue? I expected this to be a problem with the server edition of Ubuntu but I didn't expect to get totally stuck with no local prompt or ssh. I expected it to carry on booting to the usual command prompt at this point.

System:
AMD Athlon Quad-Core (5370) 2.2GHz APU
ASRock AM1B-ITX Motherboard
2xKingston ValueRAM 8GB (1x8GB) DDR3 1600MHz
Syba SATA III 4 Port PCI-e x1 Controller Card
Samsung 840 SSD
Multiple 2tb drives in a RAID array, currently disconnected.

One weird thing, in the motherboard's bios menu boot device selection I can choose from:
> ubuntu
ubuntu
AHCI: Samsung 840 EVO
Choosing the Samsung option means I boot to a typical "Insert media in boot device" type message (I forget the exact words). That seems odd. Either ubuntu option seems to work. What's that all about?


I have no clue what to do next other than format and install again, which would be a disappointing step to take.

---


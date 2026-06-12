---
title: "USB HDD disconnects when copying a file"
date: 2008-06-18
forum: General Help
---

### Post by jrz on 2008-06-18
Recently I installed Ubuntu 7.04 on my computer and encountered some intermittant failures using an external USB HDD. I thought it might be the drives fault so I purchased 2 new external 500 GB drives and found they too fail when I try to copy files to them using Ubuntu. Nearl the end of the file copy I get a message "Unsafe drive removal" but if I boot Win XP I can copy files with no problems at all. I ran the command 'lspci' and received the following output:

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

looking at my computers User's Guide I see that I have a 6 port USB 2.0 controller, and notice that I saw one entry which mentioned USB 2.0 so I tried plugging the drive into different USB ports and found one that appears to work. I'm curious as to why Ubuntu seems to identify all but one controller as USB 1.1 while WinXP does not.

Is there a way to resolve this as the only port which I found to work is on the rear and difficult to access.

Thank you.

---


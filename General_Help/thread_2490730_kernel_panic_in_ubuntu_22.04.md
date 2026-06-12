---
title: "kernel panic in ubuntu 22.04"
date: 2023-09-13
forum: General Help
---

### Post by miguel2lopezm3dev on 2023-09-13
I have a problem, since yesterday I cannot log into my Ubuntu 22.04, my computer has 2 SSD disks and I have configured double boot, for Windows 10 and Ubuntu 22.04, the grub is displayed and I can log in to Windows, but not to Ubuntu.I get the error that I attached in the image.

I've already tried everything, I ran the boot-repair from a USB but it doesn't find any damage in the grub, attached a link of a log report:
[http://paste.ubuntu.com/p/dGBJF9QsDk/]("http://paste.ubuntu.com/p/dGBJF9QsDk/I")

I have already done all the recommended processes on the following page:
[https://devicetests.com/fix-init-error-boot-ubuntuand](https://devicetests.com/fix-init-error-boot-ubuntuand) 

it remains the same, the detail is that I do not want to lose the information of a partition where I have books, courses, etc.

---

### Post by tea for one on 2023-09-13
Your boot-repair report is not available as indicated by "The Paste you are looking for does not currently exist. "
> the detail is that I do not want to lose the information of a partition where I have books, courses, etc. 
Boot into a live "Try Ubuntu" session and back up your data.

After you have finished your backups, stay in the live session and re-run the boot-repair report.
Backups are essential, even if the problem can be fixed without re-installation.

---

### Post by miguel2lopezm3dev on 2023-09-15
Thanks
Please tell me the steps to follow to make the backup, I am new to Linux and I don't know if it is possible to connect an external drive and how to make the backup

My other question is how can I save the report to an external drive?

---

### Post by tea for one on 2023-09-15
> **miguel2lopezm3dev said:**
> 
Please tell me the steps to follow to make the backup, I am new to Linux and I don't know if it is possible to connect an external drive and how to make the backup
Boot into a "Try Ubuntu" live session
Plug in your external drive (which must have a formatted partition)
The external disk should be recognised automagically
Copy your important files/folders to your external disk
> **miguel2lopezm3dev said:**
> My other question is how can I save the report to an external drive?
You save the boot-repair report to [https://paste.ubuntu.com](https://paste.ubuntu.com) as indicated during the creation of the boot-repair report.
You can save it locally if you wish via [COLOR="#0000FF"]save as[/COLOR] and nominate your target location.

---

### Post by miguel2lopezm3dev on 2023-09-15
This is the report

---

### Post by tea for one on 2023-09-16
Have you successfully backed up your Ubuntu data?

---

### Post by miguel2lopezm3dev on 2023-09-18
yes

---

### Post by tea for one on 2023-09-18
All backed up now - that allows us to try a repair without worrying about loss of data.

Deactivate, isolate or physically remove your Windows disk sda
Deactivate, isolate or physically remove your other disk sdc
We are going to remove 89 unwanted EFI entries
More info here [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

Boot into a “Try Ubuntu” live session
No need to download any software, efibootmgr is already installed
Open a terminal and enter:-
```
sudo efibootmgr -v
```
You will see all the entries from your boot-repair report lines 117 > 207.
Remove all the entries 119 > 207 via the terminal:-
```
sudo efibootmgr -b 0002 -B
```
```
sudo efibootmgr -b 0003 -B
```

I do not know the command to remove multiple entries so you may have to do this one by one by changing the boot number e.g. 0004, 0005 etc. etc.

Only entries 0000 and 0001 should remain.

It doesn’t matter if you accidentally delete all the entries because you will see a message:-
> No BootOrder is set; firmware will attempt recovery
Windows Boot manager can also be added later if required.

Close the terminal and exit the live session.
Do not attach the other drives.
Boot into your Ubuntu disk and let us know what happens?

---

### Post by miguel2lopezm3dev on 2023-09-20
I did what you asked, then I turned off the computer.
I turned it on without connecting the Windows disk, and I booted with the grub menu and Ubuntu appeared first but after clicking enter on that option to enter Ubuntu, I got the error that I attached in the file

---

### Post by MAFoElffen on 2023-09-21
On the bootup messages, it starts by doing a fsck on the filesystem... In the boot-info report of boot-repair, I see this output:
```

===================================== UEFI =====================================

BIOS/UEFI firmware: V1.06 from Insyde Corp.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0008
Timeout: 0 seconds
BootOrder: 0005,0055,0006,0001,0000,0008,0004,0003,2001,2002,2003
Boot0000* Linux    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\Boot\grubx64.efi)RC
Boot0001* Windows Boot Manager    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0002* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0003* bootwin2022    PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,0,0)/HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgr.efi)A01 ..
Boot0004* win10    PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,0,0)/HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)A01 ..
Boot0005* ubuntu2    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-00-00-00-00-00-00-00)/HD(1,GPT,53568364-e636-4f90-9b4c-63c1850ce283,0x800,0x1e8000)/File(\EFI\ubuntu\grubx64.efi)A01 ).
Boot0006* Linux    HD(1,GPT,53568364-e636-4f90-9b4c-63c1850ce283,0x800,0x1e8000)/File(\EFI\Boot\grubx64.efi)RC
Boot0007* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,53568364-e636-4f90-9b4c-63c1850ce283,0x800,0x1e8000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0008* Linux    HD(1,MBR,0x18d08107,0x800,0x1ce7800)/File(\EFI\Boot\grubx64.efi)RC
Boot0009* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot000A* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot000B* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot000C* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot000D* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot000E* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot000F* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0010* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0011* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0012* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0013* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0014* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0015* [COLOR=#ff0000]Unknown Device[/COLOR]:     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0016* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0017* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0018* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0019* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot001A* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot001B* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot001C* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot001D* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot001E* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot001F* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0020* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0021* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0022* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0023* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0024* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0025* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0026* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0027* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0028* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0029* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot002A* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot002B* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot002C* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot002D* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot002E* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot002F* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0030* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0031* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0032* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0033* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0034* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0035* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0036* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0037* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0038* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0039* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot003A* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot003B* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot003C*[COLOR=#ff0000] Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot003D* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot003E* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot003F* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0040* [COLOR=#ff0000]Unknown Device: [/COLOR]    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0041* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0042* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0043* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0044* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0045* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0046* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0047* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0048* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0049* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot004A* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot004B* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot004C* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot004D* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot004E* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot004F* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0050* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0051* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0052* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0053* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0054* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0055* Windows Boot Manager    HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0056* ubuntu    HD(1,GPT,53568364-e636-4f90-9b4c-63c1850ce283,0x800,0x1e8000)/File(\EFI\ubuntu\shimx64.efi)
Boot0135* [COLOR=#ff0000]Unknown Device:[/COLOR]     HD(1,GPT,0cdd9ecf-0396-4d27-8a8c-47f11362f905,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/BOOT/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   nvme0n1p1/BOOT/fbx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   nvme0n1p1/BOOT/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/BOOT/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   nvme0n1p1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bootx64.efi
85fa9d77b929ec4231aba29476574eb6   sda1/Boot/fbx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda1/Boot/grubx64.efi
469e608783843a701d172242f016c79c   sda1/Boot/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda1/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
b3d98a277c250e553554ddf4d7bb9ace   sda1/Microsoft/Boot/bootmgfw.efi
06523c5f4c39b3789bce23ae28c7d4d0   sda1/Microsoft/Boot/bootmgr.efi

```
Which is the same file, in the same partition, repeated 87 times... on /dev/sda1... I see a pattern there.

You see that right? When I see "unknown device" in efibootmgr results, I think of BIOS error, that a BIOS update might fix. But that may be a "false positive" result, because... Coupled with the fsck happening, and then the repeated file... I would first do a fsck.vfat on that partition first (suspected filesystem corruption), then recheck the efibootmgr -v results.

---

### Post by miguel2lopezm3dev on 2023-09-21
I don't understand what process I have to follow to run this utility: ( I would first do a fsck.vfat on that partition first (suspected filesystem corruption))  and in what partition

---

### Post by tea for one on 2023-09-21
Only have your Ubuntu disk attached
Boot into a "Try Ubuntu" live session
Open a terminal and enter:-
```
sudo umount /dev/nvme0n1p1 [COLOR="#0000FF"]#just to double-check it is not mounted[/COLOR]
```
```
sudo fsck -a /dev/nvme0n1p1
```
More light reading here [https://devicetests.com/dirty-bit-fsck-remove](https://devicetests.com/dirty-bit-fsck-remove)

---

### Post by miguel2lopezm3dev on 2023-09-25
I already carried out the requested process, as shown in image 1, then I turned off the computer and tried to boot to Ubuntu but I got this error that I attached in image 2

---

### Post by tea for one on 2023-09-25
Not making much progress so far.....

According to the boot-repair report, you have alternative kernels:-
Ubuntu, with Linux 5.19.0-50-generic  
Ubuntu, with Linux 5.15.0-78-generic 

Have you tried to boot into either of these (via Grub menu > Advanced options)?

---

### Post by miguel2lopezm3dev on 2023-09-26
Yes I tried from the beginning before contacting them and the same error came out.

---

### Post by tea for one on 2023-09-26
I think that I've just reproduced your kernel error on a test system by removing [COLOR="#0000FF"]init[/COLOR] from [COLOR="#0000FF"]/sbin/.[/COLOR]
Subsequently:-
I booted into a live session and copied the init (from the live system) to the sbin directory of the installed system.
Elevated (i.e. sudo) privileges will be needed.
My error was fixed and Ubuntu booted.

First of all, we need to establish if you have init in /sbin/ on your installed system.
Please boot into a "Try Ubuntu" live session.
Navigate via the file manager to your system partition (nvme0n1p3)
When you access /sbin/, can you see init?

---

### Post by miguel2lopezm3dev on 2023-09-28
Yes I can see the file
I attach the image

---

### Post by tea for one on 2023-09-29
Perhaps, the init file is not doing its job properly.........?

If I were in your position:-
(a) Replace the file from the live system to the installed system - just to see what happens.
(b) After two weeks without a solution, re-install and restore my backup data.

---

### Post by miguel2lopezm3dev on 2023-10-03
ok
in the case of re-install how do i do it?

---

### Post by tea for one on 2023-10-04
> **miguel2lopezm3dev said:**
> ok
in the case of re-install how do i do it?
Back up all personal data

Use your Windows OS to download Rufus [https://rufus.ie/en/](https://rufus.ie/en/)
Also download Ubuntu 22.04 iso
Create a bootable Ubuntu disk with gpt and target UEFI
Close Windows 

Useful info [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Disconnect, de-activate, isolate via UEFI settings or physically remove existing Windows OS drive so that _only the target drive_ is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
If you cannot isolate your Windows 10/11 drive, you can hide the existing EFI partition.
Gparted > Right click Windows EFI Partition > Manage Flags > Uncheck boot & esp and check hidden (msfdata will be checked automatically &#8211; not a problem)
Don&#8217;t forget to reset the flags to original settings after installing Ubuntu to 2nd disk
Allow Ubuntu installer to create an EFI System Partition and System partition
Boot loader on target disk

When installation is finished, de-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

---

### Post by miguel2lopezm3dev on 2023-10-13
Sorry for not answering, I have a question after that process that tells me how to restore my backup if the only thing I did was copy the folders to an external drive. When installing Linux, do you have to create the partitions as you originally had them? Or what is the process to follow to restore my backup?

Thanks

---


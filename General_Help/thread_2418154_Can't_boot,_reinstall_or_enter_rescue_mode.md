---
title: "Can't boot, reinstall or enter rescue mode"
date: 2019-05-02
forum: General Help
---

### Post by th3bish0p on 2019-05-02
[COLOR=#242729][FONT=Arial]Hello, since a few days, I can't boot my computer on ubuntu 18.04.2 , I can't even access rescue mode or boot on a liveusb to try to reinstall my os. Windows is booting fine however.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]On a regular ubuntu boot some services fail to start and at some point, the boot process simply stops 
[IMG]https://i.stack.imgur.com/w9RHU.jpg[/IMG]

When I try to start rescue mode or boot with liveusb, I have other messages like AMD-VI: Completion-Wait loop timed out and iommu ivhd0: Event logged [IOTLB_INV_TIMEOUT device=1b:00.0 address=0x40e596610] or Kernel panic - not syncing: corrupted stack end detected inside scheduler 
[IMG]https://i.stack.imgur.com/UfT5R.jpg[/IMG]
[IMG]https://i.stack.imgur.com/6Yhpk.jpg[/IMG]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Computer specs :[/FONT][/COLOR]

[LIST]
[*]Motherboard: b350 PC MATE (bios up-to-date) 
[*]CPU: Ryzen 5 2600X 
[*]GPU: radeon RX 570 
[*]Ubuntu 18.04.2 
[/LIST]
[COLOR=#242729][FONT=Arial]I check my hardware (memtest, gpu/cpu stress test, SMART drive check) and nothing is wrong, I event tried another graphic card. I tried to boot with ubuntu 16.04 liveusb, same issue. I tried boot options noapic, nolapic without any success, with acpi=off I have the following screen 
[IMG]https://i.stack.imgur.com/YyWBQ.jpg[/IMG]

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=inherit]I tried to boot with ubuntu daily build to have the latest kernel, but no luck.

[/FONT]Thank you for your help, I'm completly stuck I can't work anymore...


[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2019-05-02
This is worth a shot here and may sound silly>>>but, powerOFF your machine, and pull all the cables to the HardDrive (Power & Data cables) now power back on, then PowerOFF again.
Now re-connect the cables and boot-up.

---

### Post by th3bish0p on 2019-05-02
didn't change anything :(

---

### Post by #&amp;thj^% on 2019-05-02
Yikes I had just seen this on AU: [https://askubuntu.com/questions/1139350/ubuntu-cant-boot-access-rescue-mode-or-reinstall](https://askubuntu.com/questions/1139350/ubuntu-cant-boot-access-rescue-mode-or-reinstall)
> the bios was updated AFTER the issue to try to solve it. 
This is a very deep rabbit hole now....:(

---

### Post by th3bish0p on 2019-05-02
I shouldn't have updated my bios ?

---

### Post by #&amp;thj^% on 2019-05-02
Yes you should have if there was an update available and the correct Bios version was installed, but just adds to the frustrations of trying to find out why your system is, well broken.
How many hardrives are connected?
And if Windows 10 installed>>> is the appropriate settings set in the Bios?

---

### Post by th3bish0p on 2019-05-02
I have 3 harddrives : 1 SSD and 2 HDD but as you suggested to unplug every hd, I tried to boot on a liveusb without any harddrive and had the exact same issue, so I don't think it is connected to my drives, it's more a mobo/cpu issue I think.
I also tried to boot with an older GPU.
Windows 10 is installed and working fine.

---

### Post by TheFu on 2019-05-02
Way to bury the lead!

You are **running a CPU that has been available for 2-3 weeks**, correct?  Talk about bleeding edge.  Ryzen3 is completely new to the world.

Also, hopefully a MOD will convert those inline images to attachments.

My guess is that you need a BIOS update and probably will need to run the nightly kernel 5.2.x versions for a few months, if those work.

---

### Post by th3bish0p on 2019-05-02
Well my bad, I mistyped it, my cpu is a Ryzen 2600x, bought last august

---

### Post by TheFu on 2019-05-02
I have a 2600.  It has been rock solid on an Asus B450 with a slight OC running stock 16.04.6
 
I don't use Windows, but I would check for "faststart", ACHI, and verify that Windows is closing all the file systems.  I understand that Windows update, about once a year, will wipe out the grub install.  [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup) 

I'd also ensure that both OSes use the same boot method - either UEFI or Legacy, no switching necessary.  My MB has an option for Legacy boot-only, UEFI boot-only, and a UEFI on HDDs and legacy on USB.  The normal ISO file for Ubuntu Mate 16.04 is setup to boot either with UEFI or Legacy BIOS.  What is supported by your MB could be different.

I know nothing about later ubuntu distributions, but would expect the same boot capabilities.

Can't remember if I mentioned this, but there have been 2 MB firmware updates since I bought the MB+CPU in December.  They both made it more compatible with the CPU for OC (13% on the stock cooler) and RAM for 3200Mhz speeds.  Whenever a new BIOS firmware is installed, be certain to check all the BIOS options again. Sometimes they get wiped.

It doesn't crash, ever.

---

### Post by th3bish0p on 2019-05-08
Bios settings seem to be ok, bios is up-to-date.

I managed to  access a terminal (by editing a grub line, adding " 3" at the end). Now I  try to "fix" my system with apt commands. > apt update  can't reach hosts, so I think there a network issue at some point. I can  ping local or distant IP but not dns. If I try to restart  NetworkManager, it fails because of a timeout.

systemctl status NetworkManager.server :
[https://pix.toile-libre.org/upload/original/1557305128.jpg](https://pix.toile-libre.org/upload/original/1557305128.jpg)

journalctl -xe :
[https://pix.toile-libre.org/upload/original/1557305193.jpg](https://pix.toile-libre.org/upload/original/1557305193.jpg)

---


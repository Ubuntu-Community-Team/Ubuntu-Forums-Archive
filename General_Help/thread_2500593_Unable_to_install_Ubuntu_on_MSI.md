---
title: "Unable to install Ubuntu on MSI"
date: 2024-09-06
forum: General Help
---

### Post by mubashir100 on 2024-09-06
I want to dual boot my MSI with ubuntu but I am unable to do so. Currently windows 11 is installed. I partitioned the ssd. There is 150Gb for the ubuntu. I have a bootable usb with ubuntu 22.0.1 LTS. I am able to boot the os from usb but when I try to install I get "not enough storage" error I think it tries to install the os in the usb itself which is not good. 
I searched online and came across this: [https://askubuntu.com/questions/1127505/ssd-not-detected-during-ubuntu-installation](https://askubuntu.com/questions/1127505/ssd-not-detected-during-ubuntu-installation)
I am supposed to change the RAID to [COLOR=#0C0D0E][FONT=-apple-system]AHCI  but in the boot menu I the SATA option is not present. I checked by running in the safe mood as well. 
When I boot from usb I don't get the "something else " to basically choose the partition. 
what should I do? I have installed ubuntu using this usb in another system so it's not the usb issue.

Also the scale is so big that everything is goes out of the screen when I try from the usb

SYSTEM: Pulse 17 B13VGK
[/FONT][/COLOR]13th Gen Intel(R) Core(TM) i9-13900H

edit
`sudo parted -l`
I get this
Model: Kingston DT 101 G2
disk  /dev/sda: 3916MB

---

### Post by TheFu on 2024-09-06
There might be a way to use Intel RST drivers, but I've just disabled Intel RAID for AHCI and the storage was seen.  Of course, I wiped MS-Windows11 from the system.  I changed a few other BIOS settings that were Windows-specific - sorry, I don't remember all of them - and installed Linux.

USB flash compatibility isn't universal, BTW.   I have flash drives that boot perfectly in 1 computer, but not another.  I've had all sorts of these flash storage devices work and fail to work.  No-names work or fail.  Brand-names work or fail.  I've never found a pattern in over 20 yrs.  I do know that some USB controllers in some computers aren't compatible with some flash drives.  Seems pretty random to me.  In general, try a different USB port and go with USB2 ports over USB3 when troubleshooting on a specific computer.

New hardware is always a problem for Linux, since the computer vendors seldom test for Linux compatibility.  I just got a new-to-me Dell laptop that has many of the new BIOS issues.  It is an 11th-gen Core i5.  

If you can't get the storage solved - which I fear may require reinstalling MS-Windows after you change from RAID to AHCI mode - you might want to consider running Linux inside a virtual machine under MS-Windows.  I started doing that in the late 1990s.  Eventually, I started using VMs for almost everything.  Right now, as I type this, the browser I'm using is running on a different computer, inside a VM, accessed over the LAN here.  There are many reasons I do this.  VMs provide so much flexibility and remove any hardware incompatibility issues, since the VM only sees fake hardware that the hypervisor running on the real hardware provides.  Tune properly, over 90% of native performance is possible for everything except GPU-intensive workloads.

---

### Post by nicolasdentremont on 2024-09-06
> **mubashir100 said:**
> 
I am supposed to change the RAID to AHCI  but in the boot menu I the SATA option is not present.

I also had to change that in order to install Ubuntu. In my BIOS menu, the option is hidden by default. I had to show the hidden options by using "ctrl + S" I believe.  Maybe yours is similar.

---

### Post by oldfred on 2024-09-06
Make sure you have latest UEFI & SSD firmware.
Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status

You have to use a version of any distribution that is newer than you hardware to have latest kernel & drivers needed for that new hardware.
Try 24.04.1.

What video card/chip. Specs say nVidia.
You probably need to use Safe boot and install all proprietary drivers as part of install to have support for nVidia.

New Driver Aims To Improve MSI Laptop Support On Linux Feb 2023
[https://www.phoronix.com/news/MSI-EC-Laptop-Driver-Linux](https://www.phoronix.com/news/MSI-EC-Laptop-Driver-Linux)
[https://www.phoronix.com/news/Linux-6.4-MSI-EC-Driver](https://www.phoronix.com/news/Linux-6.4-MSI-EC-Driver)
MSI MS-14C6 Prestige 14Evo Core i7 1280P 22.04 but 5.18 kernel needed
[https://www.phoronix.com/review/intel-1280p-windows-linux](https://www.phoronix.com/review/intel-1280p-windows-linux)
SSD upgrade issue MSI Gaming
[https://superuser.com/questions/1530474/trying-to-upgrade-my-laptop-ssd-1mm-to-fit-in-the-slot](https://superuser.com/questions/1530474/trying-to-upgrade-my-laptop-ssd-1mm-to-fit-in-the-slot)

---

### Post by mubashir100 on 2024-09-09
I created a new bootable usb using the rufus for 24.0.4 LTS and installed the OS using that and it worked and it worked

---


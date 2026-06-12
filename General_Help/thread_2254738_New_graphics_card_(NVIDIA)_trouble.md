---
title: "New graphics card (NVIDIA) trouble"
date: 2014-11-29
forum: General Help
---

### Post by Onna_Nelson on 2014-11-29
I've been having a lot of trouble getting my new graphics card working. The full specs of my machine are:

[COLOR=#141823][FONT=Helvetica]CPU: Intel Pentium G3220 3.0GHz Dual-Core Processor [/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Motherboard: Gigabyte GA-H81M-HD3 Micro ATX LGA1150 Motherboard [/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Memory: Crucial Ballistix Sport 8GB (1 x 8GB) DDR3-1600[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Storage: PNY Optima 240GB 2.5" Solid State Drive [/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Case: Rosewill Line-M MicroATX Mini Tower Case [/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Power Supply: Corsair Builder 430W 80+ Bronze Certified ATX Power Supply [/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Wireless Network Adapter: Rosewill RNX-G300LX 802.11b/g PCI Wi-Fi Adapter [/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]GPU (added yesterday): Zotac ZT-70706-10M[/FONT][/COLOR]

When I tried to install the drivers, I was able to download and open (and possibly install?) the correct NVIDIA driver. However, nothing ever showed up on Additional Drivers and commands like 

```
[COLOR=#333333][FONT=UbuntuMono]gksudo gedit /etc/X11/xorg.conf[/FONT][/COLOR]
```

don't do anything. 

In my last thread, I had a lot of trouble getting Unity working. I finally got that working, my system seems to recognize that I have a new GPU. Doing

```
lspci -x | grep -i "vga\|display"
```

gives me both my on-board and my new GPU. I could get to the GRUB/BIOS/safe mode through the monitor's connection to the GPU, or boot normally through the mobo.

So I went into the BIOS and changed the default graphics device to PCIe16. I tried disabling onboard graphics. Now no matter what combination I have of onboard disabled/enabled or default graphics PCIe16 or IGFX (onboard), whenever I save and exit the BIOS it goes to the GRUB screen. I can't seem to get it to boot normally again.

From the GRUB screen, I'm not really sure where to go. Which options should I choose? Choosing "System Setup" takes me back to the BIOS. Choosing "Ubuntu" seems to crash (it goes to a purple screen and just hangs forever connected to the GPU, and flashes many colors connected to the mobo). Choosing "Advanced Options for Ubuntu" gives me four more options, two of which are recovery mode. All the options available in recovery mode are also overwhelming. I'm new to Linux and would really like a step-by-step guide through these options to get me back to normal desktop.


------------------ update -----------------
Whenever I try to boot via recovery mode, it reaches this point and comes up with this error:

```
 
* Starting configure virtual network devices          [OK]
* Stopping Failsafe Boot Delay                             [fail]

```

Then a few more successful *starting, followed by
```

* Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated   [OK]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
* Stopping Reload cups, upon starting avahi-daemon to make sure remote queues are populated   [OK]
[     5.344274] ata1: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[     5.344299] ata1: irq_stat 0x00400040, connection status changed 
[     5.344317] ata1: SError:   {   HostInt PHYRdyChg 10B8B DevExch   }
_

```

It totally freezes at this point and I have to hard shut down.

---

### Post by papibe on 2014-11-29
Hi Onna_Nelson.

I'd try to boot using the **nomodeset** option. Check the section 'How to temporarily set kernel boot options on an installed OS' in this [thread]("http://ubuntuforums.org/showthread.php?t=1613132") for details.

If that works, follow the steps on the next section (How to permanently set kernel boot options on an installed OS) in order to set the option for every subsequent boot.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Onna_Nelson on 2014-11-29
Thanks, but I'm really new to Linux and that thread was not helpful at all. Baby steps, or ELI5? How do I add the nomodset option? From GRUB, do I go to recovery mode and choose the root shell prompt and enter something?

Edit: [this thread had an ELI5 version I found useful.]("http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu")

---

### Post by papibe on 2014-11-29
See if this youtube video helps:  [Howto Fix Ubuntu Black Screen]("https://www.youtube.com/watch?v=OTmZYzaxR_k&feature=youtu.be&t=1m21s").

---

### Post by Onna_Nelson on 2014-11-29
**nomodese** didn't seem to help. It still hangs on the purple screen forever.

---

### Post by papibe on 2014-11-29
Try nomodeset with only the Nvidia card selected from the BIOS.

Regards.

---

### Post by Onna_Nelson on 2014-11-29
PCIe16 selected, onboard graphics disabled. Still a purple screen just hanging even with nomodeset. Am I supposed to be using nomodeset in recovery mode or the regular Ubuntu boot or...?

I honestly am not worried about data loss. I just want a working computer. I've tried a lot of "fixes" and editing and scripts and they all seem to have made everything worse (see my last thread). I tried reinstalling Ubuntu from a USB stick. I can enter the BIOS and select "boot from USB". It gives me the option to install ubuntu or try ubuntu without installing, and a couple other options. If I try installing Ubuntu, the screen goes totally black when my monitor is connected to the GPU, and flickers random colors when it's connected to the mobo.

---

### Post by papibe on 2014-11-29
I just saw your edit of original post.

This error is more likely come from a disk (or other sata device):
```
ata1: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
```
I would make sure all connections are well plugged. Or even change the sata cable to another motherboard sata port.

Let us know how it goes.
Regards.

---

### Post by oldfred on 2014-11-29
Gigabyte motherboards seem to require added boot parameters. You probably need both nomodeset for the nVidia and perhaps additional ones.
You may be able to just change UEFI/BIOS setting on iommu.

 Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

      
 Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

---


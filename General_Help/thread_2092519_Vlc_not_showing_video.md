---
title: "Vlc not showing video"
date: 2012-12-08
forum: General Help
---

### Post by Hiuhu on 2012-12-08
Hey ??
I recently installed ubuntu 12.04 in vmware successfully but there seems to be a problem with my vlc. The vlc does not display any video only playing audio. I reinstalled it and even installed the ubuntu restricted extras but no luck yet. If anyone knows how to fix this please fell free to help. Thanks in advance

---

### Post by pissedoffdude on 2012-12-08
Try looking into what video driver you have installed and if its the appropriate one.  This might be related to vmware and the current video drivers, so let us know what kind of graphics card you have as well.

---

### Post by Hiuhu on 2012-12-08
This is what the command shows me :
jemoh@G580-virtual-machine ~ $ sudo lspci -k
[sudo] password for jemoh: 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
        Subsystem: VMware Virtual Machine Chipset
        Kernel driver in use: agpgart-intel
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
        Kernel modules: shpchp
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
        Subsystem: VMware Virtual Machine Chipset
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
        Subsystem: VMware Virtual Machine Chipset
        Kernel driver in use: ata_piix
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
        Subsystem: VMware Virtual Machine Chipset

---

### Post by Hiuhu on 2012-12-08
I found the solution. Go to vlc then on tools choose preferences and on the video section change the output option to opengl

---

### Post by pissedoffdude on 2012-12-08
Are you currently getting 3d support? Also, what kind of graphics card do you have?  I think lspci should do the trick.  If it doesn't, do it outside of vmware, or use whatever operating system your using in the background to find out what kind of card you have.  Do you have the latest vmware installed by the way?

Edit:  Awesome!  Go ahead and mark this issue as solved

---


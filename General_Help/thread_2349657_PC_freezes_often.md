---
title: "PC freezes often"
date: 2017-01-17
forum: General Help
---

### Post by rolfUser on 2017-01-17
[ATTACH=CONFIG]273229[/ATTACH]
Often times, while being on Google Chrome, particularly right after I open a new tab to open a new link, my PC will slow down and basically freeze. A video will skip until it stops playing, the mouse will stop moving, not unlike something you see on Windows.

This happens often now and after turning off and turning back on again the machine, I snapped a picture of something that pops up momentarily on the screen just before the desktop appears.

What does it all mean and what can I do to fix it?

---

### Post by ajgreeny on 2017-01-17
Difficult to know what is going on from your description.

What hardware do you have, particularly the graphic chip, and what driver for that?  If you're not sure show us the output of ```
lspci -k
``` in terminal.

Does the computer shutdown properly or do you have problems and errors showing at that time?
The error showing at startup > /dev/sda5: Recovering journal suggests an unclean shutdown last time.

---

### Post by rolfUser on 2017-01-18
lspci -k
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330]
    Subsystem: Hewlett-Packard Company Kabini [Radeon HD 8330]
    Kernel driver in use: radeon
    Kernel modules: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
    Subsystem: Hewlett-Packard Company Kabini HDMI/DP Audio
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
    DeviceName:  Onboard IGD
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
    Subsystem: Hewlett-Packard Company FCH USB XHCI Controller
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
    Subsystem: Hewlett-Packard Company FCH SATA Controller [AHCI mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
    Subsystem: Hewlett-Packard Company FCH USB OHCI Controller
    Kernel driver in use: ohci-pci
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
    Subsystem: Hewlett-Packard Company FCH USB EHCI Controller
    Kernel driver in use: ehci-pci
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
    Subsystem: Hewlett-Packard Company FCH USB OHCI Controller
    Kernel driver in use: ohci-pci
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
    Subsystem: Hewlett-Packard Company FCH USB EHCI Controller
    Kernel driver in use: ehci-pci
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
    Subsystem: Hewlett-Packard Company FCH SMBus Controller
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
    Subsystem: Hewlett-Packard Company FCH Azalia Controller
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
    Subsystem: Hewlett-Packard Company FCH LPC Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---

### Post by rolfUser on 2017-01-18
No. The computer does not shut down properly. I shut it down improperly by holding down the power button on the PC's tower. The PC is too slow when it slows down to even handle a shutdown since the mouse doesn't want to move either.

The PC will just stop running if I have too much information loaded up on Google Chrome, or too many programs standing by.  I've been a linux user since Ubuntu 12.04 (I'm using 16.04 now)  and this slow-down was not always an issue.

---

### Post by HermanAB on 2017-01-18
Err... is your hard disk full?  Check with df.

---

### Post by rolfUser on 2017-01-19
df
```
Filesystem     1K-blocks      Used Available Use% Mounted onudev             1719032         0   1719032   0% /dev
tmpfs             347856     14808    333048   5% /run
/dev/sda5       19553560  16795820   1741420  91% /
tmpfs            1739264    109336   1629928   7% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            1739264         0   1739264   0% /sys/fs/cgroup
/dev/sda6      220052260 151459344  57391844  73% /home
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             347856        76    347780   1% /run/user/1000



```

---

### Post by HermanAB on 2017-01-20
OK, it looks fine, but it gets slow...

Try taking periodic snap shots with top by directing the output to a file, then doing what you normally do till it dies and on reboot look at the file:

$ top > topfile.txt

Top refreshes once a second, so it should result in a long file full of run data.  Then see if you can identify a bad program.

---

### Post by mörgæs on 2017-01-20
If you run the commands 
```
sudo apt-get clean 
sudo apt-get autoremove
``` and after that again 
```
df -h
```
what does the output now look like?

---

### Post by kostkon on 2017-01-21
Next time your PC freezes try doing a reboot using the [REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key") key combo, otherwise, judging by the screenshot you've posted, you will eventually corrupt your filesystem beyond repair.

---

### Post by rolfUser on 2017-01-22
> **mörgæs said:**
> If you run the commands 
```
sudo apt-get clean 
sudo apt-get autoremove
``` and after that again 
```
df -h
```
what does the output now look like?

sudo apt-get clean 
then...
sudo apt-get autoremove
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  guile-2.0 hyphen-en-gb libabw-0.1-1v5 libcdr-0.1-1 libcmis-0.5-5v5
  libe-book-0.1-1 libeot0 libetonyek-0.1-1 libfreehand-0.1-1 libiso9660-8
  libmlt++3 libmlt-data libmlt6 libmovit4 libmspub-0.1-1 libmwaw-0.3-3
  libodfgen-0.1-1 libopenshot9 liborcus-0.10-0v5 libpagemaker-0.0-0
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-help-ja
  libreoffice-help-ru libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-l10n-ja libreoffice-l10n-ru librevenge-0.0-0 libvcdinfo0
  libvisio-0.1-1 libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-headers-4.4.0-42
  linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-headers-4.4.0-45
  linux-headers-4.4.0-45-generic linux-headers-4.4.0-47
  linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-image-4.4.0-34-generic
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic
  linux-image-4.4.0-42-generic linux-image-4.4.0-43-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-47-generic
  linux-image-4.4.0-51-generic linux-image-4.4.0-53-generic
  linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-43-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-47-generic linux-image-extra-4.4.0-51-generic
  linux-image-extra-4.4.0-53-generic melt python-mlt python-pygoocanvas
0 upgraded, 0 newly installed, 73 to remove and 12 not upgraded.
After this operation, 2,852 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 791687 files and directories currently installed.)
Removing guile-2.0 (2.0.11+1-10) ...
Removing hyphen-en-gb (1:5.1.0-1ubuntu2.2) ...
Removing libabw-0.1-1v5:amd64 (0.1.1-2ubuntu2) ...
Removing libcdr-0.1-1:amd64 (0.1.2-2ubuntu2) ...
Removing libcmis-0.5-5v5:amd64 (0.5.1-2ubuntu2) ...
Removing libe-book-0.1-1:amd64 (0.1.2-2ubuntu1) ...
Removing libeot0:amd64 (0.01-3ubuntu1) ...
Removing libetonyek-0.1-1:amd64 (0.1.6-1ubuntu1) ...
Removing libfreehand-0.1-1:amd64 (0.1.1-1ubuntu1) ...
Removing libvcdinfo0 (0.7.24+dfsg-0.2) ...
Removing libiso9660-8:amd64 (0.83-4.2ubuntu1) ...
Removing python-mlt (6.0.0-2) ...
Removing melt (6.0.0-2) ...
Removing libmlt-data (6.0.0-2) ...
Removing libmspub-0.1-1:amd64 (0.1.2-2ubuntu1) ...
Removing libmwaw-0.3-3:amd64 (0.3.7-1ubuntu2) ...
Removing libodfgen-0.1-1 (0.1.6-1ubuntu2) ...
Removing libopenshot9:amd64 (0.1.2+0+542+103+201608300559~ubuntu16.04.1) ...
Removing liborcus-0.10-0v5:amd64 (0.9.2-4ubuntu2) ...
Removing libpagemaker-0.0-0:amd64 (0.0.3-1ubuntu1) ...
Removing libreoffice-help-en-gb (1:5.2.4~rc2-0ubuntu1~xenial2) ...
Removing libreoffice-help-en-us (1:5.2.4~rc2-0ubuntu1~xenial2) ...
Removing libreoffice-help-ja (1:5.2.4~rc2-0ubuntu1~xenial2) ...
Removing libreoffice-help-ru (1:5.2.4~rc2-0ubuntu1~xenial2) ...
Removing libreoffice-l10n-en-gb (1:5.2.4~rc2-0ubuntu1~xenial2) ...
Removing libreoffice-l10n-en-za (1:5.2.4~rc2-0ubuntu1~xenial2) ...
Removing libreoffice-l10n-ja (1:5.2.4~rc2-0ubuntu1~xenial2) ...
Removing libreoffice-l10n-ru (1:5.2.4~rc2-0ubuntu1~xenial2) ...
Removing libwps-0.4-4:amd64 (0.4.3-1ubuntu1) ...
Removing libwpg-0.3-3:amd64 (0.3.1-1ubuntu1) ...
Removing libvisio-0.1-1:amd64 (0.1.5-1ubuntu1) ...
Removing libwpd-0.10-10:amd64 (0.10.1-1ubuntu1) ...
Removing linux-headers-4.4.0-34-generic (4.4.0-34.53) ...
Removing linux-headers-4.4.0-34 (4.4.0-34.53) ...
Removing linux-headers-4.4.0-36-generic (4.4.0-36.55) ...
Removing linux-headers-4.4.0-36 (4.4.0-36.55) ...
Removing linux-headers-4.4.0-38-generic (4.4.0-38.57) ...
Removing linux-headers-4.4.0-38 (4.4.0-38.57) ...
Removing linux-headers-4.4.0-42-generic (4.4.0-42.62) ...
Removing linux-headers-4.4.0-42 (4.4.0-42.62) ...
Removing linux-headers-4.4.0-43-generic (4.4.0-43.63) ...
Removing linux-headers-4.4.0-43 (4.4.0-43.63) ...
Removing linux-headers-4.4.0-45-generic (4.4.0-45.66) ...
Removing linux-headers-4.4.0-45 (4.4.0-45.66) ...
Removing linux-headers-4.4.0-47-generic (4.4.0-47.68) ...
Removing linux-headers-4.4.0-47 (4.4.0-47.68) ...
Removing linux-headers-4.4.0-51-generic (4.4.0-51.72) ...
Removing linux-headers-4.4.0-51 (4.4.0-51.72) ...
Removing linux-headers-4.4.0-53-generic (4.4.0-53.74) ...
Removing linux-headers-4.4.0-53 (4.4.0-53.74) ...
Removing linux-image-extra-4.4.0-34-generic (4.4.0-34.53) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-34-generic (4.4.0-34.53) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-extra-4.4.0-43-generic (4.4.0-43.63) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-43-generic (4.4.0-43.63) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-extra-4.4.0-47-generic (4.4.0-47.68) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-47-generic (4.4.0-47.68) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-47-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-extra-4.4.0-51-generic (4.4.0-51.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-53-generic (4.4.0-53.74) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing python-pygoocanvas (0.14.1-1.1ubuntu1) ...
Removing librevenge-0.0-0:amd64 (0.0.4-4ubuntu1) ...
Removing libmlt++3 (6.0.0-2) ...
Removing libmlt6 (6.0.0-2) ...
Removing libmovit4:amd64 (1.3.1-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...

```

---

### Post by rolfUser on 2017-01-22
df -h
```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.7G     0  1.7G   0% /dev
tmpfs           340M   11M  330M   4% /run
/dev/sda5        19G   12G  5.8G  68% /
tmpfs           1.7G  184M  1.5G  11% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/sda6       210G  146G   54G  73% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           340M   68K  340M   1% /run/user/1000

```

---

### Post by rolfUser on 2017-01-22
before (1/20/2017)
df
```

Filesystem     1K-blocks      Used Available Use% Mounted onudev             1719032         0   1719032   0% /dev
tmpfs             347856     14808    333048   5% /run
/dev/sda5       19553560  16795820   1741420  91% /
tmpfs            1739264    109336   1629928   7% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            1739264         0   1739264   0% /sys/fs/cgroup
/dev/sda6      220052260 151459344  57391844  73% /home
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             347856        76    347780   1% /run/user/1000

```

after (1/22/2017)
df -h
```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.7G     0  1.7G   0% /dev
tmpfs           340M   11M  330M   4% /run
/dev/sda5        19G   12G  5.8G  68% /
tmpfs           1.7G  184M  1.5G  11% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/sda6       210G  146G   54G  73% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           340M   68K  340M   1% /run/user/1000

```

So what was wrong and what happened?

---

### Post by mörgæs on 2017-01-22
The sda5 partition was 91% full which is much too high. The commands deleted unneeded and obsolete stuff. I recommend that you get into the habit of running them say every other week. 

Is the computer more stable now?

---

### Post by ajgreeny on 2017-01-22
With all those linux-header packages now removed it is quite possible, or perhsps probable that had you run the command df -i```

``` you might have had an even higher %age figure for sda5 of inodes used and maybe absolutely none remaining unused.

Each linux-header package adds many thousands of small files to your system and it is they which use a lot of inodes.

---

### Post by rolfUser on 2017-01-22
As the out output popped up in the terminal, It looked recursive and I thought it would never stop. The sign of a computer virus? I haven't turned off my computer to restart. I'm afraid it might be the last time and will need to find a technician to fix it.

I once installed Ubuntu Tweak on another PC with Ubuntu 12.04 dual-booted w/Windows 7.  When I used the janitor to clean unnecessary files, the cleaning was successful but it would be the last time that partition was used. It was never a priority to fix that but I keep it in mind. Now it is only used for Windows 7. 

On the PC I'm using where I'm having this problem that you're helping me with, it's dual-booted with Windows 10, as you can see, and I upgraded from 14.04 to 16.04 last year.

 on the way to the upgrade, there were... maybe 2 prompts  --   asking if I want to keep the same [system?] files or replace them with new ones. I think I kept the same ones -- but when the upgrade was finished, I couldn't open Steam. LibreOffice was stuck with the custom theme I installed previously. I couldn't delete and reinstall, and I opened a new thread to fix that.
[https://ubuntuforums.org/showthread.php?t=2335418](https://ubuntuforums.org/showthread.php?t=2335418)

Today I'm afraid of what could happen if I do a cleaning with Janitor after this upgrade (14.04 --> 16.04). Hopefully nothing will go wrong.
If you need me to open a new thread to investigate the matter -- the matter of why Steam does not open, if that is connected in some way to this discussion -- Let's do that.

---

### Post by Yellow Pasque on 2017-01-22
> As the out output popped up in the terminal, It looked recursive and I thought it would never stop. The sign of a computer virus?
No. That's just how it goes when you remove a bunch of old kernels in one shot (and yes, it takes a while).

I wouldn't use the "Janitor" program. I never heard good things about it..

---

### Post by rolfUser on 2017-01-22
> **Temüjin said:**
> No. That's just how it goes when you remove a bunch of old kernels in one shot (and yes, it takes a while).

I wouldn't use the "Janitor" program. I never heard good things about it..

I never had a problem with Janitor when PC was running 14.04. 
Can you elaborate on what you're saying?

---

### Post by rolfUser on 2017-01-22
> **mörgæs said:**
> The sda5 partition was 91% full which is much too high. The commands deleted unneeded and obsolete stuff. I recommend that you get into the habit of running them say every other week. 

Is the computer more stable now?
Although the problem was something that interrupts the PCs performance abruptly, I would say that video streams are noticeably running smoother.  My only concern now is if it truly is safe to restart this PC -- if there is anything else that needs to be examined.

---

### Post by Yellow Pasque on 2017-01-22
> **rolfUser said:**
> I never had a problem with Janitor when PC was running 14.04. 
Can you elaborate on what you're saying?

I just remember some bad stories about the program being overzealous and removing software that users wanted to keep (especially stuff from PPA's). To be fair, this was several years ago, so it's possible that it improved since then.

>  My only concern now is if it truly is safe to restart this PC -- if there is anything else that needs to be examined. 

What exactly is your concern? You still have the current kernel and one previous one, as well as a 3.13 kernel leftover from Trusty that you can remove.

```
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
```

---

### Post by blackneos940 on 2017-01-22
I've had that happen before on my Chromebook, and on another Laptop.....   :)   For whatever reason, Chrome was using up too much RAM.....   :\   It turns out that, at least on my Laptop with a Hard Disk, Hardware Acceleration was turned on.....   :)   When I disabled it, the problem disappeared!.....   :D   Let me know if this works for you!.....   :)   Good Luck!!.....   ^^

Something to add to this Post.....   While Chrome was causing the lag, the HDD light on the side of my Laptop was on like CRAZY.....   :(   This indicated that it was being **CONSTANTLY** used.....   :)

---

### Post by blackneos940 on 2017-01-22
> **rolfUser said:**
> As the out output popped up in the terminal, It looked recursive and I thought it would never stop. The sign of a computer virus?

:)

Linux is designed to be secure, so while it's HIGHLY, **HIGHLY** unlikely that you'll **EVER** get a Virus, it is possible, I suppose.....   :)  But, as someone else said on here, you're good.....   :D

---

### Post by mörgæs on 2017-01-23
Please reboot. There is nothing indicating boot problems.

I think this is a lesson about not upgrading. When you decide to go to 18.04 LTS I recommend a fresh install. 

Why do you want to run Janitor when you have the two commands shown?

---


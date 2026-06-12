---
title: "Uefi"
date: 2014-12-28
forum: General Help
---

### Post by lizard2014 on 2014-12-28
Hello. We are having a new computer which has windows 8 pre loaded. When we install Ubuntu, the ubuntu's grub boot loader seems to be absent (maybe due to UEFI). How do I cure this ?

---

### Post by oldfred on 2014-12-28
Often grub is installed into UEFI partition, but you still have to select to boot it as it now is one of many options in UEFI menu. Both UEFI boot choices and one time boot key often f12 or f10 may also give same choices.

What brand/model system, and what video card/chip?
Some vendors modify UEFI to only boot UEFI entry with "Windows" in description and we have to create work arounds, some better than others depending on configuration or system.

Just to confirm every thing is installed. Do not run any auto fix until someone has reviewed report.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by lizard2014 on 2014-12-29
[TABLE="class: tableBg"]
[TR]
[TD="class: tdBg, colspan: 3"]Well, I don't understand much of all this, but here are all the specifications of our device

[SIZE=6] _**HP 14-r054TU Notebook Computer.**_[/SIZE]
OS
[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Operating system[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Windows 8.1 64[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]Processor[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Processor[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Intel® Core&#8482; i3-4005U with Intel HD Graphics 4400 (1.7 GHz, 3 MB cache, 2 cores)[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]MEMORY[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Memory, standard[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 4 GB 1600 MHz DDR3L SDRAM (1 x 4 GB)[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]STORAGE[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Hard drive description[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 1 TB 5400 rpm SATA[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]OPTICAL DISK DRIVE[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Optical drive[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 SuperMulti DVD burner[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]GRAPHICS[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Graphics[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Intel HD Graphics 4400[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]Display[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Display[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 14" diagonal HD BrightView WLED-backlit (1366 x 768)[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Display size (diagonal)[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 14"[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]Connectivity[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Expansion slots[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 1 multi-format SD media card reader[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Network interface[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Integrated 10/100 BASE-T Ethernet LAN[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Wireless[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 802.11b/g/n (1x1) and Bluetooth® 4.0 combo[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]Ports/Slots[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Ports[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 1 USB 3.0; 2 USB 2.0; 1 HDMI; 1 VGA; 1 RJ-45; 1 headphone/microphone combo[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]INPUT[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Webcam[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 HP TrueVision HD Webcam (front-facing) with integrated digital microphone[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Keyboard[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Full-size textured island-style[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Pointing device[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Touchpad with multi-touch gesture support[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]Audio[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Audio features[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Dual speakers[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]POWER[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Power supply type[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 65 W EM AC power adapter[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Battery type[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 4-cell (41 WHr) Li-ion[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]SECURITY[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Security management[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Kensington MicroSaver  lock slot; Power-on password; Accepts third-party security lock devices[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]MACHINE DIMENSIONS & WEIGHT[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Weight[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 Starting at 1.96 kg[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Minimum dimensions (W x D x H)[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 34.5 x 24.4 x 2.53 cm[/TD]
[/TR]
[TR]
[TD="class: tdBg, colspan: 3"]Warranty[/TD]
[/TR]
[TR]
[TD="class: tdBgWhite"]Warranty[/TD]
[TD="class: tdBgRightWhite, colspan: 2"]                                                 1-year limited parts and labour[/TD]
[/TR]
[/TABLE]

---

### Post by lizard2014 on 2014-12-29
Ah ! Thats awesome ! I just posted some lines and it automatically detected them and created a table.

---

### Post by oldfred on 2014-12-29
HP often will only boot the UEFI entry with Windows in decription. There are several work arounds. Most with dual booting create or rename the /EFI/Boot/bootx64.efi file to really be grub and create or boot the hard drive entry in UEFI menu.

And Intel often needs boot parameter to correctly load video mode. Nomodeset usually does not work with Intel, but you add parameters the same way. See ubfan1's post for several alternatives.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

      
 Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)


 Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

---


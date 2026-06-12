---
title: "High Temperature after cleaning with Bleachbit"
date: 2015-03-02
forum: General Help
---

### Post by docdoc2 on 2015-03-02
I thought it might be a good idea to use bleachbit in order to get rid of some private data and get some free space, but after using it my laptop sounds like a vacuum cleaner. Even after booting its very loud, but i cant really see any high cpu usage. Only chromium and compiz but only about 10%. But Bleachbit didnt touch chromium! 

Is there a way to make my laptop silent again? I dont want to format everything.

---

### Post by gifford on 2015-03-02
What version of Ubuntu are you using?
Is it your fan making the noise?
Give some specifics on your laptop as well.

---

### Post by sammiev on 2015-03-02
Bleachbit has to be used carefully, it's known to do extra house cleaning causing unwanted issues. Before doing anything, backup all your data.

---

### Post by docdoc2 on 2015-03-03
Well, i do not know how this could have happened. Yes it is the fan, temperatures are high as hell, i hope my computer wont melt. Htop and system monitor dont show very high cpu usage though.

Bleachbit couldn't delete some files because of missing permissions, maybe i should clean again as root?

Current Bleachbit configuration (it might have changed, not sure):
APT
-clean
Deep scan
-temporary files
-thumbs.db
Flash
-Cache
-Cookies
System
-Broken Desktop files
-Cache
-Temporary files

Ubuntu 14.04 (trusty)
GNOME 3.8.4
Kernel 3.13.0-46-generic

lspci> 00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev ff)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
0a:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)

---

### Post by docdoc2 on 2015-03-19
Can no one help me to find the culprit? The machine is running damn hot (~75°) and fans are at high speed constantly. This did not happen before, unless i converted a video or so. htop does not show major cpu usage. Also, i use the recommended nvidia driver, but it seems to make no difference which one i choose. even after booting and without any program running its like that.

---

### Post by dino99 on 2015-03-19
you should be fine; i'm a user of bleachbit as root, since a couple years. I am carefull when it is time to check/uncheck options; but yours looks good anyway.
run it 'as root'
if the logs does not complaint about errors/warnings, then it could be your own profile being borked; save it with the date extension for example, then reboot to create an other one to see if it help

---

### Post by mastablasta on 2015-03-19
install lmsensors or just psensor to see the temperature. if CPU is not working and if cooling of CPU is good then it's the GPU that is making the noise. it could be you deleted some GPU config file.


dont' know how you installed the drivers, but did you purge them completely and attempted a reinstall?

---


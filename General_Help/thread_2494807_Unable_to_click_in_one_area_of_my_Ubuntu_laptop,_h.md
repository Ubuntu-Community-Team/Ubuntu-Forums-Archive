---
title: "Unable to click in one area of my Ubuntu laptop, how can i find which app is affect?"
date: 2024-01-27
forum: General Help
---

### Post by namastepritish on 2024-01-27
I recently installed Ubuntu on my asus r558ur laptop, 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293358&stc=1[/IMG]

AS per image attached above, the highlighted area is top right of my ubuntu desktop env. 
So far I've tried: 
1. Moving top panel to bottom using this extension if in case panel or other extension causing issue ([https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/) ) but I'm still unable to click in that area. 
2. I installed anydesk app just in case if that causing any issue, after quitting the app from panel and all background activity still result is same 


Update: This problem is not related to just chrome, no matter i put terminal /console in this place or any other app in that place, I'm simply unable to click or inface click there and move the window as well. so its now become dark spot for clicking for me. 

cat /etc/os-release
```
PRETTY_NAME="Ubuntu 23.10"NAME="Ubuntu"
VERSION_ID="23.10"
VERSION="23.10 (Mantic Minotaur)"
VERSION_CODENAME=mantic
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=mantic
LOGO=ubuntu-logo



```

lspci output 
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Skylake GT2 [HD Graphics 520] (rev 07)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 930MX] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter



```

---

### Post by jeremy31 on 2024-01-27
the only thing i can think of is to open termina and run ```
xev
```
Drag the event tester terminal box to that area and see if any errors show in the main terminal window when you click in the event tester box

---

### Post by namastepritish on 2024-01-27
Below is the output when i took the window to that area, after that nothing is coming on the screen when i click on the window, the moment i took the windows from that area some output starts generating. But there was no error into that region
ConfigureNotify event, serial 38, synthetic YES, window 0x3600001,
    event 0x3600001, window 0x3600001, (1737,73), width 178, height 178,
    border_width 2, above 0x0, override NO


ConfigureNotify event, serial 38, synthetic YES, window 0x3600001,
    event 0x3600001, window 0x3600001, (1738,73), width 178, height 178,
    border_width 2, above 0x0, override NO


ConfigureNotify event, serial 38, synthetic YES, window 0x3600001,
    event 0x3600001, window 0x3600001, (1739,73), width 178, height 178,
    border_width 2, above 0x0, override NO


FocusIn event, serial 38, synthetic NO, window 0x3600001,
    mode NotifyUngrab, detail NotifyNonlinear


KeymapNotify event, serial 38, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

---


---
title: "using external usb wifi adapter?"
date: 2024-11-16
forum: General Help
---

### Post by garyed on 2024-11-16
I have an old laptop running ubuntu 22.04 release with a very slow internal wifi connection. 
I wanted to try an external usb wifi adapter to see if I can up the speed of my wifi so I tried an old usb adapter that I used to use on another ubuntu computer. 
The problem is I can't figure out how to get the computer to use it instead of the internal wifi.
lsusb : shows the usb wireless adapter so it is recognized to some degree.  
Does anyone know how I can tell Ubuntu to use the usb adapter & disable the internal wifi without physically removing it?

---

### Post by jeremy31 on 2024-11-16
Post results from terminal for ```
lsmod | grep cfg; lspci -nnk |grep -iA3 net
```

---

### Post by grahammechanical on 2024-11-16
May I suggest? That you enter the BIOS/UEFI settings and disable the internal WiFi adapter. Then Ubuntu may notice the WiFi adapter plugged into a USB port.

Regards

---

### Post by garyed on 2024-11-16
> **jeremy31 said:**
> Post results from terminal for ```
lsmod | grep cfg; lspci -nnk |grep -iA3 net
```

snd_intel_dspcfg       36864  1 snd_hda_intel
snd_intel_sdw_acpi     16384  1 snd_intel_dspcfg
cfg80211             1327104  3 rt2x00lib,rtlwifi,mac80211
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        DeviceName: Realtek PCIe FE Family Controller
        Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:3577]
        Kernel driver in use: r8169
        Kernel modules: r8169
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
        DeviceName: Realtek RTL8188CE 802.11b/g/n WiFi Adapter
        Subsystem: Hewlett-Packard Company RTL8188CE 802.11b/g/n WiFi Adapter [103c:1629]
        Kernel driver in use: rtl8192ce
--------------------------------------
Here is also the output of lsusb:

Bus 003 Device 002: ID 058f:a001 Alcor Micro Corp. HP Webcam-101                                                                      
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                                        
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                        
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                        
Bus 001 Device 002: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter                                                     
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                                        
Bus 002 Device 002: ID 25a7:fa67 Areson Technology Corp 2.4G Receiver                                                                 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by jeremy31 on 2024-11-16
```
echo "blacklist rtl8192ce"|sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo depmod -a
```
Reboot

---

### Post by garyed on 2024-11-16
> **grahammechanical said:**
> May I suggest? That you enter the BIOS/UEFI settings and disable the internal WiFi adapter. Then Ubuntu may notice the WiFi adapter plugged into a USB port.

Regards

I tried that but my BIOS doesn't give me an option to disable the built in wifi. 
I plan open up the laptop & pull out the wifi card if I can't find a way to do it through the software.
On a side note since your user name is grahammechanical, you might be interested in some of the HVAC calculators on this site: [https://www.oceanhvac.com](https://www.oceanhvac.com)

---

### Post by garyed on 2024-11-16
> **jeremy31 said:**
> ```
echo "blacklist rtl8192ce"|sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo depmod -a
```
Reboot
That got rid of my internal wifi adapter but now I have no internet access at all from my laptop. 
Before I go any furthe, what is the command to take it off the blacklist in case I want it back. 
It was usable before but just very slow so i want to try the usb adapter to see if it will be faster.

---

### Post by jeremy31 on 2024-11-16
```
sudo rm /etc/modprobe.d/rtl8192ce.conf
```
That will unblacklist the driver

See if this gets the USB going ```
sudo modprobe rt2800usb
```

---

### Post by garyed on 2024-11-16
> **jeremy31 said:**
> ```
sudo rm /etc/modprobe.d/rtl8192ce.conf
```
That will unblacklist the driver

See if this gets the USB going ```
sudo modprobe rt2800usb
```

That did the trick & thanks for all the help.
Before I mark this thread solved, there is a down side that I'm assuming is the fault of either an inferior usb wifi adapter or a usb limitation or both. 
It seems my internal wifi would only give about 25 to 30 Mbps & my usb adapter is even worse at about 10 to 15 Mbps.
I know the internal used to go a lot faster but this is the first time I've tried a usb adapter on this laptop.
It might be because it looks like I'm running on usb 1.1 with this old computer.

---

### Post by jeremy31 on 2024-11-16
You may want to try unplugging plugging in that dongle and see if it works on its own
I wonder if the speed is the result of wifi power management, it can be disabled with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by garyed on 2024-11-16
> **jeremy31 said:**
> You may want to try unplugging plugging in that dongle and see if it works on its own
I wonder if the speed is the result of wifi power management, it can be disabled with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

Before I try that command I'd like to know how to reverse that command in case I want to put things back to where they were originally.

---

### Post by jeremy31 on 2024-11-17
To reverse, you just change the 2 and 3 around in the command
```
sudo sed -i 's/wifi.powersave = 2/wifi.powersave = 3/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by garyed on 2024-11-17
> **jeremy31 said:**
> To reverse, you just change the 2 and 3 around in the command
```
sudo sed -i 's/wifi.powersave = 2/wifi.powersave = 3/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Thanks, 
I tried changing the poweresave to 3 & it seems to have helped a little but it's hard to be sure since bandwidth speeds can vary during different times of the day. 
I now get 35 Mbps on my internal which is still better than the usb adapter so I think I'll live with that. 
I have tried replacing my internal wifi card but after two different cards I ordered would not work I gave up with that idea. 
Just for reference my laptop is an old Compaq Presario CQ57 running Lubuntu LXQT 22.04 & my other wifi devices get well over 200 Mbps on the same router.

---

### Post by jeremy31 on 2024-11-17
See the wireless script link in my signature and post results

---


---
title: "No sound"
date: 2018-06-13
forum: General Help
---

### Post by ordak on 2018-06-13
Hi,

I have Ubuntu 16.04, on an ASUS laptop. Suddenly I have no Sound from *mp3* and *video clips* with different players. Note that the sound  is *not* muted. What can I do ?

---

### Post by ordak on 2018-06-15
By the way, if I do the following:

PulseAudio - Output Devices

There is only one device here called "Dummy Output". Is my Sound card missing here ?

---

### Post by ordak on 2018-06-16
I tried

```
aplay -l
```

Output is


```
aplay: device_list:268: no soundcards found...
```

---

### Post by ordak on 2018-06-17
After running the command :

```
discover
```

I get :

```
Atheros Communications Inc. AR9565 Wireless Network Adapter 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Linux Foundation 3.0 root hub 
unknown unknown 
unknown unknown 
Realtek Semiconductor Corp. RTS5129 Card Reader Controller 
Pixart Imaging, Inc. Optical Mouse 
Linux Foundation 2.0 root hub 


```

---

### Post by lx2kwm on 2018-06-17
i have the same after uopgrade yesterday to 18.04 from 17.10...

lx2kw@blacks:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
lx2kw@blacks:~$ 

and dummy sound in the graphical interface , didn't find the solution intil today
laptop is acer aspire 5735Z
Hans

---

### Post by ordak on 2018-06-18
Another command :

```
mehdi@mehdi-X556UQK:~$ sudo lspci
[sudo] password for mehdi: 
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940MX] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)


```

---

### Post by ordak on 2018-06-19
Maybe the problem is in latest kernel **4.4.0-128-generic** .I tried to use an older kernel, but I ran into boot problems .Should I wait for newer kernels to be distributed ?

---

### Post by ordak on 2018-06-19
I followed [this link]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS"), downloaded and installed .deb files, but still sound card is not recognized.

---


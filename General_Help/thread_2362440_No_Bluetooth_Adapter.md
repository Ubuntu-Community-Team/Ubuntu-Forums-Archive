---
title: "No Bluetooth Adapter"
date: 2017-05-28
forum: General Help
---

### Post by luketdavis1 on 2017-05-28
Hi,

fairly new to Ubuntu (and linux in general) I have installed Ubuntu on my Lenovo x1 Carbon

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

I have installed blueman however I cannot get my bluetooth to work

Error received: 
I can turn on however when I select "Add device" I get error: No Adapter Found

I know I have bluetooth adapter built in as previously used in Windows


```
luke@luke-ThinkPad-X1-Carbon:~$ cd /var/log
luke@luke-ThinkPad-X1-Carbon:/var/log$ grep -i firmware syslog*
syslog:May 24 19:13:44 luke-ThinkPad-X1-Carbon kernel: [45868.523251] [drm] GuC firmware load skipped
syslog:May 24 19:13:44 luke-ThinkPad-X1-Carbon kernel: [45869.527980] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 24 19:13:44 luke-ThinkPad-X1-Carbon kernel: [45869.527993] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 24 19:13:44 luke-ThinkPad-X1-Carbon kernel: [45869.527994] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 24 19:13:44 luke-ThinkPad-X1-Carbon kernel: [45869.551050] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 24 19:13:44 luke-ThinkPad-X1-Carbon kernel: [45869.551063] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 24 19:13:44 luke-ThinkPad-X1-Carbon kernel: [45869.551065] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 24 20:43:29 luke-ThinkPad-X1-Carbon kernel: [49538.719666] [drm] GuC firmware load skipped
syslog:May 24 20:43:29 luke-ThinkPad-X1-Carbon kernel: [49539.735343] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 24 20:43:29 luke-ThinkPad-X1-Carbon kernel: [49539.739085] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 24 20:43:29 luke-ThinkPad-X1-Carbon kernel: [49539.739089] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 24 20:43:29 luke-ThinkPad-X1-Carbon kernel: [49539.757464] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 24 20:43:29 luke-ThinkPad-X1-Carbon kernel: [49539.757478] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 24 20:43:29 luke-ThinkPad-X1-Carbon kernel: [49539.757479] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 25 15:11:28 luke-ThinkPad-X1-Carbon kernel: [52913.308294] [drm] GuC firmware load skipped
syslog:May 25 15:11:28 luke-ThinkPad-X1-Carbon kernel: [52914.331671] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 25 15:11:28 luke-ThinkPad-X1-Carbon kernel: [52914.331685] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 25 15:11:28 luke-ThinkPad-X1-Carbon kernel: [52914.331686] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 25 15:11:28 luke-ThinkPad-X1-Carbon kernel: [52914.338707] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 25 15:11:28 luke-ThinkPad-X1-Carbon kernel: [52914.338726] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 25 15:11:28 luke-ThinkPad-X1-Carbon kernel: [52914.338728] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 25 19:15:48 luke-ThinkPad-X1-Carbon kernel: [53695.219645] [drm] GuC firmware load skipped
syslog:May 25 19:15:48 luke-ThinkPad-X1-Carbon kernel: [53696.223501] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 25 19:15:48 luke-ThinkPad-X1-Carbon kernel: [53696.226894] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 25 19:15:48 luke-ThinkPad-X1-Carbon kernel: [53696.226898] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 25 19:15:48 luke-ThinkPad-X1-Carbon kernel: [53696.248337] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 25 19:15:48 luke-ThinkPad-X1-Carbon kernel: [53696.248350] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 25 19:15:48 luke-ThinkPad-X1-Carbon kernel: [53696.248351] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 26 18:07:15 luke-ThinkPad-X1-Carbon kernel: [56224.862511] [drm] GuC firmware load skipped
syslog:May 26 18:07:15 luke-ThinkPad-X1-Carbon kernel: [56225.888525] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 26 18:07:15 luke-ThinkPad-X1-Carbon kernel: [56225.889710] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 26 18:07:15 luke-ThinkPad-X1-Carbon kernel: [56225.889714] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 26 18:07:15 luke-ThinkPad-X1-Carbon kernel: [56225.900708] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
syslog:May 26 18:07:15 luke-ThinkPad-X1-Carbon kernel: [56225.900723] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
syslog:May 26 18:07:15 luke-ThinkPad-X1-Carbon kernel: [56225.900724] Bluetooth: hci0: Failed to load Intel firmware file (-2)
syslog:May 26 18:07:24 luke-ThinkPad-X1-Carbon gnome-session[3120]: (gnome-software:3295): GsPlugin-WARNING **: Failed to download [https://s3.amazonaws.com/lvfsbucket/downloads/firmware.xml.gz.asc](https://s3.amazonaws.com/lvfsbucket/downloads/firmware.xml.gz.asc), ignoring: Cannot resolve hostname
```


```
luke@luke-ThinkPad-X1-Carbon:~$ sudo lspci 
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:08.0 System peripheral: Intel Corporation Sky Lake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Device 9d12 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (4) I219-V (rev 21)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
04:00.0 Network controller: Intel Corporation Device 24fd (rev 88)
05:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 0115 (rev 01)
```
```
luke@luke-ThinkPad-X1-Carbon:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0097 Validity Sensors, Inc. 
Bus 001 Device 003: ID 04f2:b5ce Chicony Electronics Co., Ltd 
Bus 001 Device 011: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by jeremy31 on 2017-05-28
In terminal do
```
cd /lib/firmware/intel
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/intel/ibt-12-16.ddc
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/intel/ibt-12-16.sfi
```

Reboot

---


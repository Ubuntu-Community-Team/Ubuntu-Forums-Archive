---
title: "Fingerprint reader detected but not working"
date: 2016-04-27
forum: General Help
---

### Post by Salil_Surendran on 2016-04-27
Hello,
   I am using Lenovo ThinkPad p50 that has a fingerprint reader which is detected but when I enter 'fprintd-enroll' it says no devices listed:

```
salilsurendran@salilsurendran-ThinkPad-P50:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:0090 Validity Sensors, Inc. [COLOR=#ff0000]<-- fingerprint sensor[/COLOR]
Bus 001 Device 002: ID 04ca:7058 Lite-On Technology Corp. 
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
salilsurendran@salilsurendran-ThinkPad-P50:~$ sudo fprintd-enroll
[sudo] password for salilsurendran: 
list_devices failed: No devices available
```

---

### Post by QDR06VV9 on 2016-04-27
For this device Validity Sensors, Inc
You will have to compile the driver by hand. 
Here is the source for the driver: [Here]("https://github.com/rayl/vfs101driver/tarball/master")
To compile it.
cd to the downloaded source file and run the below one command at a time
```
tar -xzf rayl-vfs101driver-f00e93a.tar.gz
cd rayl-vfs101driver-f00e93a
make
sudo make install
```
Regards

---

### Post by vladimiro1 on 2016-05-23
Hello.

I have the same problem on X1 carbon 4gen and 16.04 ubuntu. My device version: Bus 001 Device 008: ID **138a:0090** Validity Sensors, Inc.
I tried to compile rayl-vfs101driver-f00e93a, but I was not succesful (for example not compatible libusb.h, and so on). 
Is there some way to solve working fingerprint for this sensor?

Thanks a lot.

---

### Post by Linuxisfast on 2016-05-23
Have you tried fingerprint-gui, works like a charm on my x220.

---

### Post by vladimiro1 on 2016-05-23
Hello, 

yes I tried Fingerprint GUI. Status is the same unknown device for validity sensors. 
I suppose the source files and compilations for Ubuntu 16.04 could be a solution, since the new version of fprintd is still not available. 

```
root:~# lsusb | grep 138a:0090
Bus 001 Device 008: ID 138a:0090 Validity Sensors, Inc. 

root:~# lsusb -s 138a:0090 -v
- nothing displayed and supported

root:~# dpkg -l fprintd
  Name                                        Version                    Architecture               Description
ii  fprintd                                     0.6.0-1                    amd64                      D-Bus daemon for fingerprint reader access

root:~# dpkg -l fingerprint-gui
   Name                                        Version                    Architecture               Description
ii  fingerprint-gui                             1.07-dfsg1-0ppa1~xenial1   amd64                      application for fingerprint-based authentication
```


Thanks for help.

---

### Post by QDR06VV9 on 2016-05-23
This script will install a driver for 138a:0018 and 138a:0017 Validity Sensors, Inc. Fingerprint scanner.

Script here: [https://drive.google.com/file/d/0B45BtdjLNFQCaE5HZXgtcjhSeFE/view?pref=2&pli=1](https://drive.google.com/file/d/0B45BtdjLNFQCaE5HZXgtcjhSeFE/view?pref=2&pli=1)

Source and instructions:    [http://askubuntu.com/questions/442838/driver-for-validity-sensors-fingerprint-scanner](http://askubuntu.com/questions/442838/driver-for-validity-sensors-fingerprint-scanner)

Credit To: prakharsingh95

---

### Post by vladimiro1 on 2016-05-23
Hi,

I suppose, that driver for **138a:0018** and **138a:0017** Validity Sensors doesn't support my current **138a:0090** driver/version :(.

The existing version of libfprint0 (from standard ubuntu repository):
```
root:~# dpkg -l libfprint0
   Name                                        Version                    Architecture               Description
ii  libfprint0                                  1:0.6.0-git20151216-1-0ppa amd64                      fingerprint library of fprint project, shared libraries

```

I would be happy if my X1 Carbon 4 gen with last Ubuntu 16.04 support operational fingerprint. Any idea?

Thanks.

---

### Post by hacker-cb on 2016-06-06
I have Lenovo ThinkPad X1 Yoga with "138a:0090 Validity Sensors, Inc" fingerprint reader and it also not work.

---

### Post by gprather on 2016-07-06
Has there been any update on the drivers for the 138a:0090? Running a P50 and haven't been able to get fprint, fingerprint-gui or rayl-vfs101driver-f00e93a to work.

---

### Post by QDR06VV9 on 2016-07-06
Do not shoot the messenger;)
Bug 94536 - 138a:0090 Validity Sensor not recognized
[URL="https://bugs.freedesktop.org/show_bug.cgi?id=94536"]https://bugs.freedesktop.org/show_bug.cgi?id=94536

>            Vasily Khoruzhick                                                  2016-06-08 00:47:42 UTC                      [/URL]Sorry guys, but I don't have this device. And even if I had it, I'm not sure what can be done if traffic is encrypted.
I tried to contact Synaptics (they acquired Validity not a while ago), but so far I have gotten no response.[URL="https://bugs.freedesktop.org/show_bug.cgi?id=94536"][SIZE=2][/SIZE]
[/URL]

---

### Post by mathew.chacko on 2017-04-09
Same here. It is not working for Yoga 260 :(

---


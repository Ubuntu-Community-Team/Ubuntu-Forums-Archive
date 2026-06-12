---
title: "Script not running automatically on usb dongle insert"
date: 2015-03-15
forum: General Help
---

### Post by Akash_Yadav on 2015-03-15
My objective is to run the script automatically when usb-dongle is inserted . I looked into other links for the same but just can't get it work . 
Script is running fine manually but doesn't run when usb dongle is inserted . 

Below are the files for the same .  Please someone suggest what am i missing ?


1. 
meher@meher-Compaq-620:~$ lsusb
Bus 002 Device 011: ID 12d1:14db Huawei Technologies Co., Ltd. 

2.   Script is 

meher@meher-Compaq-620:~$ ls -lrt ~/mtsdongle.sh
-rwxrwxrwx 1 root root 92 Mar 11 22:27 /home/meher/mtsdongle.sh
meher@meher-Compaq-620:~$ cat ~/mtsdongle.sh
#! /bin/sh
notify-send "****** <MTS DONGLE INSERTED> *****"
env > /tmp/env.out
echo "akash"
meher@meher-Compaq-620:~$ 

3. rules is 

 meher@meher-Compaq-620:/etc/udev/rules.d$ pwd
 /etc/udev/rules.d

 meher@meher-Compaq-620:/etc/udev/rules.d$ ls -lrt

 total 8
 -rwxrwxrwx 1 root root 116 Mar 11 22:32 77-mts.rules
 meher@meher-Compaq-620:/etc/udev/rules.d$ cat 77-mts.rules

 ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="12d1", ATTR{idProduct}=="14db", RUN+="/home/meher/mtsdongle.sh"

---

### Post by Akash_Yadav on 2015-03-16
[COLOR=#000000]Any help to this problem would be appreciated.[/COLOR]

---


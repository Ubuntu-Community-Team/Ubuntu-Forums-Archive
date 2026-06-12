---
title: "Rasberry Pi 3 Model B+ cannot setup WiFi on Ubuntu server 20.04"
date: 2021-06-28
forum: General Help
---

### Post by bomberb17 on 2021-06-28
I flashed Ubuntu server 20.04 image on my Pi 3 Model B+.
However I can't get WiFi to work at all.
I run 
```
sudo nano /boot/firmware/network-config
``` and this is the file I have:

```
version: 2
ethernets:
  eth0:
    dhcp4: true
    optional: true
wifis:
  wlan0:
    dhcp4: true
    optional: true
    access-points:
      "mySSIDname":
        password: "mywifipassword"

``` and  ```
$ ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether b8:27:eb:8b:91:a9 brd ff:ff:ff:ff:ff:ff
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000
    link/ether b8:27:eb:de:c4:fc brd ff:ff:ff:ff:ff:ff

``` Why wlan0 stays down? Am I doing something wrong?

---

### Post by TheFu on 2021-06-29
I have no clue about running Ubuntu on ARM, but the normal location for netplan config files is /etc/netplan/.
I always found Ubuntu to be too heavy for use on a Pi and used raspbian instead.

To reduce my ignorance, I searched and found this: [https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#3-wifi-or-ethernet](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#3-wifi-or-ethernet)
That pages says the file is in the "system-boot" directory, but I couldn't figure out where that actually was based on the instructions.  

My best guess would be **[COLOR="#00FF00"]/boot/network-config[/COLOR]**, but the mounted location for the sdcard under the other system would make that a little different.

I think having both ethernet and wifi configured concurrently is a bad idea. Disable the one you won't be using.

---


---
title: "problemwith external hard drive . please help:("
date: 2007-03-18
forum: General Help
---

### Post by raffytaffy on 2007-03-18
ve been having issues with the external mounting on start up ( out of every 10 times it wont mount maybe 2 time) .
this HD is sda on my system. i used the command dmesg to see for any possible errors...and sure enough i found some:|

[ 3110.624000] sd 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3110.624000] Additional sense: Logical unit not ready, initializing command required
[ 3110.624000] end_request: I/O error, dev sda, sector 0
[ 3110.624000] Buffer I/O error on device sda, logical block 0
[ 3110.631000] sd 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3110.631000] Additional sense: Logical unit not ready, initializing command required
[ 3110.631000] end_request: I/O error, dev sda, sector 0
[ 3110.631000] Buffer I/O error on device sda, logical block 0
[ 3110.637000] sd 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3110.637000] Additional sense: Logical unit not ready, initializing command required
[ 3110.637000] end_request: I/O error, dev sda, sector 0
[ 3110.637000] Buffer I/O error on device sda, logical block 0
[ 3110.637000] Buffer I/O error on device sda, logical block 1
[ 3110.637000] Buffer I/O error on device sda, logical block 2
[ 3110.637000] Buffer I/O error on device sda, logical block 3


here is my df -h

raf@Equinox:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/hda1 54G 20G 32G 39% /
varrun 506M 100K 506M 1% /var/run
varlock 506M 4.0K 506M 1% /var/lock
procbususb 506M 188K 506M 1% /proc/bus/usb
udev 506M 188K 506M 1% /dev
devshm 506M 0 506M 0% /dev/shm
/dev/hda2 18G 7.1G 11G 40% /media/hda2
/dev/sdb1 233G 94G 140G 41% /media/My Book
/dev/sdc1 299G 77G 222G 26% /media/WD Combo
/dev/sda5 192G 97G 96G 51% /media/usbdisk
/dev/sda6 41G 8.0K 41G 1% /media/usbdisk-1

what can i do...as you can see i have some data on the drive itself and dont wanna loose it.

---


---
title: "XSane: wifi scanner / Invalid parameter"
date: 2020-07-14
forum: General Help
---

### Post by alain.roger on 2020-07-14
Hi,

my friend has a wifi scanner Brother DCPL 2530 DW that prints without any error. It also scanned without any issue, however for some unknown reason it stopped to scan and raises an error message while using XSANE "invalid parameter"

i did a test using brsaneconfig4 and output iscorrect:
```
[FONT=monospace][COLOR=#000000]-----------------------------[/COLOR]
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=0a33edc3-b084-4c1f-ac92-ff6881ef47cf /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=2300-AD3A  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
-----------------------------
sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x1d6b/0x0003 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x0bda/0x0129 at 001:005: Access denied (insufficient permissions)
could not open USB device 0x04f2/0xb64a at 001:004: Access denied (insufficient permissions)
could not open USB device 0x03f0/0x1198 at 001:003: Access denied (insufficient permissions)
could not open USB device 0x13d3/0x3490 at 001:006: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
-----------------------------
ls -R -all /proc/bus/usb
ls: cannot access '/proc/bus/usb': No such file or directory
-----------------------------
cat /proc/bus/usb/devices
cat: /proc/bus/usb/devices: No such file or directory
-----------------------------
scanimage -L
device `escl:http://192.168.0.100:80' is a ESCL Brother DCP-L2530DW series flatbed scanner
-----------------------------
-----------------------------
/etc/opt/brother/scanner/brscan4//brsanenetdevice4.cfg:
-----------------------------
/etc/opt/brother/scanner/brscan4//Brsane4.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_2.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_24.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_7.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_20.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_19.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_23.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_12.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_4.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_17.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_13.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_5.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_14.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_9.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_22.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_16.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_10.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_18.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_3.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_15.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_6.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_21.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_11.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_8.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_1.ini:
-----------------------------
-----------------------------
ping
test DCPL2530DW
ping 192.168.0.100 -w 10

PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
64 bytes from 192.168.0.100: icmp_seq=1 ttl=255 time=2.60 ms
64 bytes from 192.168.0.100: icmp_seq=2 ttl=255 time=85.8 ms
64 bytes from 192.168.0.100: icmp_seq=3 ttl=255 time=23.6 ms
64 bytes from 192.168.0.100: icmp_seq=4 ttl=255 time=2.82 ms
64 bytes from 192.168.0.100: icmp_seq=5 ttl=255 time=171 ms
64 bytes from 192.168.0.100: icmp_seq=6 ttl=255 time=91.1 ms
64 bytes from 192.168.0.100: icmp_seq=7 ttl=255 time=2.58 ms
64 bytes from 192.168.0.100: icmp_seq=8 ttl=255 time=33.3 ms
64 bytes from 192.168.0.100: icmp_seq=9 ttl=255 time=7.12 ms
64 bytes from 192.168.0.100: icmp_seq=10 ttl=255 time=62.7 ms

--- 192.168.0.100 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 2.576/48.216/170.609/52.138 ms[/FONT]
```


I can run the scanning application, however when i launch a scan, application raises error message "invalid parameters".
I tried to change the resolution to 100, 200, 300 and 600 but nothing helps.

Any idea what could be the issue ?
thx

---


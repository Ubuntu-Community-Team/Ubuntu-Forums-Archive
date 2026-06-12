---
title: "Usbip Windows server and linux client version mismatched. What to do to match them ?"
date: 2020-04-29
forum: General Help
---

### Post by marietto2008 on 2020-04-29
Hello.

Actually I'm enjoying with WSL2. I would like to use my XBOX / KINECT within WSL2 / Ubuntu.

To do that,I need to make in communication the USB ports of the usbip client which run in Linux with the usbip server which run on Windows. This is exactly what the project below does :

[https://github.com/cezanne/usbip-win](https://github.com/cezanne/usbip-win)

These are the usb device address of my PC :

usbip.exe list -l -

busid 1-129 (05e3:0608) Genesys Logic, Inc. : Hub (05e3:0608)
busid 1-167 (05e3:0608) Genesys Logic, Inc. : Hub (05e3:0608)
busid 1-149 (0480:a007) Toshiba America Inc : External Disk USB 3.0
(0480:a007)
busid 1-175 (2109:0813) VIA Labs, Inc. : unknown product (2109:0813)
busid 1-89 (2109:2813) VIA Labs, Inc. : unknown product (2109:2813)
busid 1-220 (25a7:fa23) unknown vendor : unknown product (25a7:fa23)
busid 1-177 (048d:8297) Integrated Technology Express, Inc. : unknown
product (048d:8297)
busid 1-122 (1058:0704) Western Digital Technologies, Inc. : My Passport
Essential (WDME) (1058:0704)
busid 1-43 (2109:0813) VIA Labs, Inc. : unknown product (2109:0813)
busid 1-144 (05ac:0250) Apple, Inc. : Aluminium Keyboard (ISO) (05ac:0250)
busid 1-184 (1058:25a3) Western Digital Technologies, Inc. : unknown
product (1058:25a3)
busid 1-218 (2109:2813) VIA Labs, Inc. : unknown product (2109:2813)
busid 1-209 (045e:02c4) Microsoft Corp. : unknown product (045e:02c4)
busid 1-181 (0480:a207) Toshiba America Inc : unknown product (0480:a207)
busid 1-29 (093a:2510) Pixart Imaging, Inc. : Optical Mouse (093a:2510)
busid 1-134 (0bc2:61b5) Seagate RSS LLC : unknown product (0bc2:61b5)
busid 1-158 (05ac:1006) Apple, Inc. : Hub in Aluminum Keyboard (05ac:1006)

I went on a real linux installation for understand what's the address of my XBOX :

[ 2.392735] usb 2-8: new SuperSpeed Gen 1 USB device number 4 using xhci_hcd
[ 2.413596] usb 2-8: New USB device found, idVendor=045e, idProduct=02c4,
bcdDevice= 1.00
[ 2.413596] usb 2-8: New USB device strings: Mfr=1, Product=2,
SerialNumber=4
[ 2.413597] usb 2-8: Product: Xbox NUI Sensor
[ 2.413597] usb 2-8: Manufacturer: Microsoft

given that informations,this is what I did on windows 10 :

C:\Users\marietto2020\Desktop\WSL\Kinect\usbip-win (master -> origin)
&#955; usbip.exe bind -b 1-209
usbip: info: bind_device: bind device on busid 1-209: complete

C:\Users\marietto2020\Desktop\WSL\Kinect\usbip-win (master -> origin)
&#955; usbipd -d -4
usbipd: info: starting usbipd (usbip 1.0.0)
usbip: debug:
C:\work\usbip-win\userspace\src\usbipd\usbipd_sock.c:38:[build_sockfd]
opening 0.0.0.0:3240
usbip: info: listening on 0.0.0.0:3240

instead,this is what I did on Ubuntu 20 :

root@DESKTOP-N9UN2H3:/mnt/c/Users/marietto2020/Desktop/WSL/WSL/Ubuntu-KVM/WSL2-Linux-Kernel/tools/usb/usbip#
usbip attach -r 192.168.1.6 -b 1-209
usbip: error: Attach Request for 1-209 failed - Request Completed
Successfully

this is what happens when the linux client connects to the Windows server :

usbip: info: connection from 192.168.1.6:51470
usbip: debug:
C:\work\usbip-win\userspace\lib\usbip_network.c:156:[usbip_net_recv_op_common]
version mismatch: 4353 273
usbip: debug:
C:\work\usbip-win\userspace\src\usbipd\usbipd_accept.c:18:[recv_pdu]
recv_pdu: could not receive opcode: 0

In short terms usbipd denies if protocol versions mismatched. Infact the usbip version that I use inside WSL2 is :

root@DESKTOP-N9UN2H3:/mnt/i/macos-haxm# usbip version

usbip (usbip-utils 2.0)

instead,the windows version is 0.1.0,got from here :

[https://github.com/cezanne/usbip-win/releases](https://github.com/cezanne/usbip-win/releases)

What should I do to make it work ? what's the easier way ? To use another version of usbip in Linux or in Windows ?

Where I can find the source code of usbip for Windows and for Linux ? I suppose that I need to find the versions that match.

I need that someone compiles the same version of usbip for Windows that we run on WSL2,I suppose this version :

root@DESKTOP-N9UN2H3:/mnt/i/macos-haxm# usbip version
usbip (usbip-utils 2.0)

this goes beyond my abilities. Thanks.

---


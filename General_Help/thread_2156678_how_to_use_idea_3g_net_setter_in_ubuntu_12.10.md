---
title: "how to use idea 3g net setter in ubuntu 12.10"
date: 2013-06-22
forum: General Help
---

### Post by AbhimanyuAryan on 2013-06-22
i have a internet usb stick and i want to install its software but i am able to do so i followed the video below but got no success 

----------http://www.youtube.com/watch?v=dkxNaMnafzo

he is able to install it correctly after dragging the Linux_install file to terminal where as i get an error:bash: /home/cooldudeabhi/Desktop/install_linux: Permission denied

i have the files in linux folder all which are required but i can't explore my net setter via ubuntu becoz its an auto run.exe which ubuntu doesn't support

So,  this is what i did plugged my idea net setter went straight to  terminal.....i am not logged in as root but i typed sudo su and then  password then i dragged install_linux in terminal and hit enter>this  is the message i got:bash: /home/cooldudeabhi/Desktop/install_linux: Permission denied  
 

i read it some where that u have to mount ur net setter is  it?i don't know how to mount it there's no option of mounting  it when i right click on drive......plz help me out i am very irritated but still want to use  ubuntu

also i got suggestion that who have to fix the permissions but as u can see in attached screenshots there are no permissions:(
PLZ PLZ PLZ PLZ PLZ help me out:(:(:(

---

### Post by grahammechanical on 2013-06-22
If you are able to drag the file install_linux into the terminal, then it follows that you have accessed the USB stick with the file manager. That has mounted the USB stick. I see that you have put that Linux Mobile Partner folder on your desktop as shown in the video. So, file install_linux is in that folder.

If you select it with file manager and right click it you can do two things. You can open that file with a text editor or browser and then read what it says. I am guessing that it is a set of instructions. The second things you can do is open its properties (bottom of the menu) from there you can set the permissions. It is the permissions of the file that you may need to set - not the permissions of the USB stick.

You may need to be administrator to do this. So, in a terminal type

```
gksudo nautilus &
```

That will open file manager with administrator privileges. Try to install using the file manager with administrator permissions both to set the permissions of that file and to drag it into the terminal.

Other than that this is a how to use a USB wireless stick with Ubuntu 12.10 question. Another method is to use the software centre to install Windows Wireless Drivers (ndiswrapper) and use that. Once it is installed load it and direct it to the USB stick. It might find what it needs and install it for you. I have never down this so I cannot direct you further.

Regards.

---

### Post by varunendra on 2013-06-22
> **grahammechanical said:**
> Another method is to use the software centre to install Windows Wireless Drivers (ndiswrapper) and use that. Once it is installed load it and direct it to the USB stick.

As far as I know, ndiswrapper is only meant for wireless network adapter drivers. 3g modems are all handled by the "option" driver which is always included in the kernel, but may not be aware of the device id of the modem in question.

@ Abhimanyu,

I have personally used Idea Net Setter in the past but they keep changing the device so can't say how well the current ones are supported (the earlier ones I used were all very well supported, including a 7+ Mb/s speed one).

Also, I personally have always had problems in installing the included version of Mobile Partner on it. It always gave me errors while installing and often had wierd issues, like opening the browser as "root" and using root's home for downloading stuff. I guess it was my fault though, but it suggests that you shouldn't try to install as root, if possible (that is, don't use sudo to run its installer). Because running the browser as root is one of the highest security risks.

That said, I now prefer to not use third party modem managers like Mobile Partner due to the problems I faced with them. I just use Ubuntu's default Network Manager to use 3g modems (I'm currently using an unlocked 3g modem of BSNL (micromax)). Although the Mobile Partner, if can be installed successfully, really has some cool features.

Let us first see if your modem is detected as a modem or not in the first place. Please plug the modem, wait for about 6-10 seconds, then run the following commands in the terminal -
```
lsusb
dmesg | tail -20
usb-devices
```

The command usb-devices will return a long list of info about every usb device attached. We are interested in only the modem related part. So if you can identify it, just post that part only. If not sure, post the whole output.

While posting the outputs, please use 'Code' tags (follow the link in my signature to see how).

---

### Post by AbhimanyuAryan on 2013-06-23
i am not a pro but did exactly what u said got this:   cooldudeabhi@cooldudeabhi-Studio-1450:~$ lsusb Bus 001 Device 003: ID 0c45:6407 Microdia  Bus 002 Device 007: ID 12d1:1436 Huawei Technologies Co., Ltd.  Bus 004 Device 009: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth) Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 010: ID 413c:8161 Dell Computer Corp. Integrated Keyboard Bus 004 Device 011: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics] Bus 004 Device 012: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth cooldudeabhi@cooldudeabhi-Studio-1450:~$ dmesg | tail -20 [ 3659.562710] usb 2-6: New USB device strings: Mfr=4, Product=3, SerialNumber=0 [ 3659.562714] usb 2-6: Product: HUAWEI Mobile [ 3659.562718] usb 2-6: Manufacturer: HUAWEI Technology [ 3659.565764] option 2-6:1.0: GSM modem (1-port) converter detected [ 3659.565953] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB0 [ 3659.567556] cdc_ether 2-6:1.1: wwan0: register 'cdc_ether' at usb-0000:00:1d.7-6, Mobile Broadband Network Device, 02:50:f3:00:00:00 [ 3659.567922] option 2-6:1.3: GSM modem (1-port) converter detected [ 3659.568067] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB1 [ 3659.568319] option 2-6:1.4: GSM modem (1-port) converter detected [ 3659.568385] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB2 [ 3659.568869] scsi29 : usb-storage 2-6:1.5 [ 3659.569372] scsi30 : usb-storage 2-6:1.6 [ 3660.573032] scsi 29:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2 [ 3660.573089] scsi 30:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2 [ 3660.579201] sr1: scsi-1 drive [ 3660.581911] sr 29:0:0:0: Attached scsi CD-ROM sr1 [ 3660.583063] sr 29:0:0:0: Attached scsi generic sg2 type 5 [ 3660.584360] sd 30:0:0:0: Attached scsi generic sg3 type 0 [ 3660.587826] sd 30:0:0:0: [sdb] Attached SCSI removable disk [ 3663.313239] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready cooldudeabhi@cooldudeabhi-Studio-1450:~$ usb-devices

---

### Post by AbhimanyuAryan on 2013-06-23
the above1 is confusing so i am attaching screenshots have a look at them

---

### Post by varunendra on 2013-06-23
> **AbhimanyuAryan said:**
> cooldudeabhi@cooldudeabhi-Studio-1450:~$ dmesg | tail -20
....
[ 3659.565764] option 2-6:1.0: GSM modem (1-port) converter detected
[ 3659.565953] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB0
[ 3659.567556] cdc_ether 2-6:1.1: wwan0: register 'cdc_ether' at usb-0000:00:1d.7-6, Mobile Broadband Network Device, 02:50:f3:00:00:00
[ 3659.567922] **option 2-6:1.3: GSM modem (1-port) converter detected**
[ 3659.568067] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB1
[ 3659.568319] option 2-6:1.4: GSM modem (1-port) converter detected
[ 3659.568385] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB2
[ 3659.568869] scsi29 : usb-storage 2-6:1.5 [ 3659.569372] scsi30 : usb-storage 2-6:1.6
[ 3660.573032] scsi 29:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 3660.573089] scsi 30:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 3660.579201] sr1: scsi-1 drive [ 3660.581911] sr 29:0:0:0: Attached scsi CD-ROM sr1
[ 3660.583063] sr 29:0:0:0: Attached scsi generic sg2 type 5
[ 3660.584360] sd 30:0:0:0: Attached scsi generic sg3 type 0
[ 3660.587826] sd 30:0:0:0: [sdb] Attached SCSI removable disk
[ 3663.313239] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
It seems the modem is recognised correctly, and the driver "option" is loaded for it.

When you connect it, wait a few seconds, then click on the Network Manager icon at the top-right corner. See if it shows an option to setup a "New Mobile Broadband Connection" (or something like that). It should. If it does show that option, clicking on it would let you setup your connection within the Network Manager.

Who is your service provider by the way? Idea??

---

### Post by AbhimanyuAryan on 2013-06-23
thanks varun u made my day.....i am able to connect it.....from upper right corner no installation via terminal know i have no reason of switching back to windows....thanks again bro

---

### Post by varunendra on 2013-06-23
> **AbhimanyuAryan said:**
> thanks varun u made my day.....i am able to connect it.....

You're welcome buddy ! :)

Be aware though that it would be much better if you could install Mobile Partner successfully. Because Network Manager can not provide facilities like balance check and sms sending/receiving. But if you wish to try its installation, you should try it on live sessions first. Because trying to install Mobile Partner may make the modem disappear from Network Manager. So only try if you know for sure how to install it successfully.

And if you are satisfied with the solution you currently have, please consider marking the thread as [SOLVED].

Thanks ! :)

---


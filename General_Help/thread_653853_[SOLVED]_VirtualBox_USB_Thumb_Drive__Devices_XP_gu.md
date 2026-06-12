---
title: "[SOLVED] VirtualBox USB Thumb Drive / Devices XP guest"
date: 2007-12-30
forum: General Help
---

### Post by hebetude on 2007-12-30
Error Scenarios:
run: **VBoxManage list usbhost** if your usb devices come up as unavailable then you also have this bug.


```
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}
```or
```

Failed to attach the USB device

```Note these are Ubuntu & Ubuntu Gutsy 7.10 problems not problems with VirtualBox.  Give it a spin in VMware or Qemu same problems there.  

You need to do exactly two things to resolve this USB problem with a XP guest and Ubuntu host.  Hopefully, this is a permanent solution unlike the /etc/fstab hack, I rebooted a few times and it still seems to work correctly.

**Note**:    Please, please don't change the usb mode to 0666.  This completely defeats the security implementations of linux.  Thats a Microsoft feature/fix not real Linux fix.  :)

**Step 1**: Ubuntu Gutsy 7.10 only, skip to step 2 for Feisty.
First off, we need to tell Ubuntu to mount usb devices the old way.


sudo nano -w /etc/init.d/mountdevsubfs.sh


Search for magic, it should read like this:
```

 # Magic to make /proc/bus/usb work
 #
 #mkdir -p /dev/bus/usb/.usbfs
 #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
 #ln -s .usbfs/devices /dev/bus/usb/devices
 #mount --rbind /dev/bus/usb /proc/bus/usb

```uncomment it to read:
```
 # Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

```**Step 2**: This was taken from the VirtualBox wiki for 7.04.
Edit the rules file:
sudo nano -w  /etc/udev/rules.d/40-permissions.rules

Search for:
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                    MODE="0664"
```Change it to read:
```

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", GROUP="vboxusers", MODE="0664"
```Now, go into System > Administration > Users and Groups.  Create the usbusers group and add yourself (and root if you want) to the group.

**Step 3**: If you are already a member of vboxusers, then just run the following command to reinitialize the permissions file you edited:
# /etc/init.d/mountdevsubfs.sh stop
# /etc/init.d/mountdevsubfs.sh start

If you have added yourself to vboxusers since last reboot, just logout and back in to become a member of that group.  You should be able to see available/busy status instead of 'Unavailable' when querying your usb devices.

# VBoxManage list usbhost

```

Host USB Devices:

UUID:               064dd230-a7f6-49c6-deac-f21d717f7adc
VendorId:           0x046d (046D)
ProductId:          0xc111 (C111)
Revision:           9.41 (0941)
Manufacturer:       Harmony Remote 0-2.6.0
Product:            Harmony Remote 0-2.6.0
Address:            /proc/bus/usb/005/004
Current State:      Available

UUID:               e8f5ea1c-5158-4192-c28e-b26b045fe452
VendorId:           0x046d (046D)
ProductId:          0xc521 (C521)
Revision:           87.1 (8701)
Manufacturer:       Logitech
Product:            USB Receiver
Address:            /proc/bus/usb/005/003
Current State:      Busy

UUID:               2acbbbcd-f47a-47be-edb1-ada555b72272
VendorId:           0x064e (064E)
ProductId:          0xa101 (A101)
Revision:           1.0 (0100)
Manufacturer:       SuYin
Product:            HP Webcam
SerialNumber:       CN0314-OV01-VH-R03.02.02
Address:            /proc/bus/usb/004/004
Current State:      Busy

```

**Reference**:
[http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)
**LaunchPad**:
[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085)

---

### Post by hebetude on 2007-12-30
You MUST unhook/rehook special USB devices after starting the Virtual Machine.  Otherwise, Linux kernel will grab them and not share.  This of course does not effect your standard keyboard/mouse input devices, except maybe special windows interoperability with them.

---

### Post by bengalsfan74 on 2008-03-01
Just a question, but couldn't you just use GROUP="vboxusers" rather than going through the hassle of creating a brand new group? Since everyone that is going to use VirtualBox on the machine already has to be a member of that group, it seems it'd be an easier implementation.

---

### Post by mmaki on 2008-03-04
bengalsfan74 is correct. I just did 

```
SUBSYSTEM=="usb_device", GROUP="vboxusers", MODE="0664"
```

on 7.10 and it worked without reboot.

---

### Post by hebetude on 2008-03-08
Thanks for responding, I actually use the vboxusers method now I updated the tutorial to reflect that.  

I spent another 4hours in hardy wandering the internet to fix these issues and ended up fixing it by reading my own tutorial.  I refined a few things in the tutorial, you don't need to reboot for anything now.  

Yay for documentation!

---

### Post by nikhilm on 2008-03-11
hebetude,

thanks for posting this guide- it was exactly what i was looking for. however, after following your instructions i get this error when i run vboxmanage list usbhost:


```
[!] FAILED calling Host->GetUSBDevices(CollPtr.asOutParam()) at line 1863!
[!] Primary RC  = 0x80004001
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x8000FFFF
[!] Text        = The object is not ready
[!] Component   = Progress, Interface: IProgress, {10cc03a1-717e-429b-992d-c67b56175a51}
[!] Callee      = IHost, {81729c26-1aec-46f5-b7c0-cc7364738fdb}
```

i'm running gutsy.

any idea what's gone wrong?

---

### Post by jordanius on 2008-03-16
Same problem here with the "failed calling host" error, guys - any ideas?

---

### Post by omegamormegil on 2008-03-28
I'm still getting 4/5 USB devices saying they are unavailable after running "VBoxManage list usbhost".  I'm running the Hardy beta.  I had this fixed and working in Gutsy, but now I can't seem to get the fix to take.  Any ideas?

---

### Post by omegamormegil on 2008-03-28
Ah, my problem was that a Hardy bug was preventing me from adding groups properly.  I added the usbusers group from the command line and that seems to have fixed it.

---

### Post by theZoid on 2008-04-10
Wheres' the create "usbusers' and add yourself?  Not needed anymore?  I've done his a dozen times successfully in the past.  Thanks

---

### Post by ktulu1115 on 2008-05-05
I've been trying it with vboxusers and no luck.  Also tried fiddling with /etc/fstab to add the different USB mountpoint as I saw suggested in Gutsy but to no avail.

LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
					MODE="0664", GROUP="vboxusers"

~$ id
uid=1000() gid=1000() groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(vboxusers),1000(),2000(admin)

~$ VBoxManage list usbhost
VirtualBox Command Line Management Interface Version 1.6.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Host USB Devices:

UUID:               7b4395ba-0321-42bd-95b0-9afc3a651c5f
VendorId:           0x03f0 (03F0)
ProductId:          0x3a11 (3A11)
Revision:           1.0 (0100)
Manufacturer:       hp
Product:            officejet 5500 series
SerialNumber:       MY43NF11MP96
Address:            /proc/bus/usb/001/005
Current State:      Busy

UUID:               bb8ca037-3f55-419c-eda0-1c727fea8721
VendorId:           0x0403 (0403)
ProductId:          0xc630 (C630)
Revision:           1.8 (0108)
Manufacturer:       Till Harbaum
Product:            LCD2USB Interface
Address:            /proc/bus/usb/001/004
Current State:      Unavailable

UUID:               9f612412-8c4c-4dd8-cbb9-2de7171dab48
VendorId:           0x046d (046D)
ProductId:          0xc50e (C50E)
Revision:           37.0 (3700)
Manufacturer:       Logitech
Product:            USB Receiver
Address:            /proc/bus/usb/001/008
Current State:      Unavailable

UUID:               0b494fea-74df-4477-41bd-318645075a9a
VendorId:           0x058f (058F)
ProductId:          0x6362 (6362)
Revision:           1.0 (0100)
Manufacturer:       Generic
Product:            Mass Storage Device
SerialNumber:       058F312D81B1
Address:            /proc/bus/usb/001/003
Current State:      Unavailable

UUID:               2c788d76-41ff-4df6-a780-924a80875eb5
VendorId:           0x413c (413C)
ProductId:          0x2010 (2010)
Revision:           2.0 (0200)
Manufacturer:       Dell
Product:            Dell USB Keyboard
Address:            /proc/bus/usb/001/007
Current State:      Unavailable


I don't see what difference the name makes, as long as you belong to that group, and have it set correctly in udev, right?

---

### Post by theZoid on 2008-05-05
> **ktulu1115 said:**
> I've been trying it with vboxusers and no luck.  Also tried fiddling with /etc/fstab to add the different USB mountpoint as I saw suggested in Gutsy but to no avail.

LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
					MODE="0664", GROUP="vboxusers"

~$ id
uid=1000() gid=1000() groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(vboxusers),1000(),2000(admin)

~$ VBoxManage list usbhost
VirtualBox Command Line Management Interface Version 1.6.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Host USB Devices:

UUID:               7b4395ba-0321-42bd-95b0-9afc3a651c5f
VendorId:           0x03f0 (03F0)
ProductId:          0x3a11 (3A11)
Revision:           1.0 (0100)
Manufacturer:       hp
Product:            officejet 5500 series
SerialNumber:       MY43NF11MP96
Address:            /proc/bus/usb/001/005
Current State:      Busy

UUID:               bb8ca037-3f55-419c-eda0-1c727fea8721
VendorId:           0x0403 (0403)
ProductId:          0xc630 (C630)
Revision:           1.8 (0108)
Manufacturer:       Till Harbaum
Product:            LCD2USB Interface
Address:            /proc/bus/usb/001/004
Current State:      Unavailable

UUID:               9f612412-8c4c-4dd8-cbb9-2de7171dab48
VendorId:           0x046d (046D)
ProductId:          0xc50e (C50E)
Revision:           37.0 (3700)
Manufacturer:       Logitech
Product:            USB Receiver
Address:            /proc/bus/usb/001/008
Current State:      Unavailable

UUID:               0b494fea-74df-4477-41bd-318645075a9a
VendorId:           0x058f (058F)
ProductId:          0x6362 (6362)
Revision:           1.0 (0100)
Manufacturer:       Generic
Product:            Mass Storage Device
SerialNumber:       058F312D81B1
Address:            /proc/bus/usb/001/003
Current State:      Unavailable

UUID:               2c788d76-41ff-4df6-a780-924a80875eb5
VendorId:           0x413c (413C)
ProductId:          0x2010 (2010)
Revision:           2.0 (0200)
Manufacturer:       Dell
Product:            Dell USB Keyboard
Address:            /proc/bus/usb/001/007
Current State:      Unavailable


I don't see what difference the name makes, as long as you belong to that group, and have it set correctly in udev, right?

Follow the instructions (link in my sig to get usb devices working....applies to gutsy and hardy.....hth

---


---
title: "[SOLVED] Getting a printer (usb) to work in a Virtual Machine"
date: 2007-12-29
forum: General Help
---

### Post by IanB2 on 2007-12-29
I've managed to install VM server console and create a windows 98 machine to run those applications that others in my household cannot live without.

The only fly in the ointment is that I cannot get USB devices to be recognised (and therefore cannot get a printer to work from my windows 98 VM.)

I have switched off the hot-plugged feature for removable devices and have also followed the two suggested fixes at [http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3890874](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3890874). None of this appears to have worked (I have rebooted the VM several times and also my Ubuntu host to make sure).

I have managed to get usb support working when I build a VM but using Windows XP as the host system,  so I know it can be done ....... how do you achieve usb support in Gusty for VMware?

(I've also built a windows 98 VM in Virtualbox, but virtualbox unfortunately does not support differing screen resolutions and I'm stuck with the base 480 x 600)

If usb support is not possible in VMware, is there another way of connecting a printer via the printer port direct into the VM?

---

### Post by IanB2 on 2007-12-31
Someone has suggested I try qemu.

I've had several attempts at trying to create a VM using qemu.

I keep encountering an error 'cannot install windows 98 on your computer. A disk error was detected while writing a new boot record to your first hard disk'

I've been googling to try and find a 'how to' create a windows 98 VM within qemu ..... I guess I've just got the wrong settings .... can anyone help please?

---

### Post by dcstar on 2007-12-31
> **IanB2 said:**
> 
........
I have managed to get usb support working when I build a VM but using Windows XP as the host system,  so I know it can be done ....... how do you achieve usb support in Gusty for VMware?

(I've also built a windows 98 VM in Virtualbox, but virtualbox unfortunately does not support differing screen resolutions and I'm stuck with the base 480 x 600)

If usb support is not possible in VMware, is there another way of connecting a printer via the printer port direct into the VM?

Boot the vm, then VM-Removable Devices-USB Devices and tick the ones that you want to "steal" from the host o/s.

---

### Post by IanB2 on 2007-12-31
> **dcstar said:**
> Boot the vm, then VM-Removable Devices-USB Devices and tick the ones that you want to "steal" from the host o/s.

Unfortunately the list of devices is always empty despite following the two suggested fixes

---

### Post by dcstar on 2008-01-01
> **IanB2 said:**
> Unfortunately the list of devices is always empty despite following the two suggested fixes

You have to edit /etc/init.d/mountdevsubfs.sh to make USB devices available to vmware, have you done this?

Anyway, there is a specific "Virtualization" forum in the "Other Community" section that is more appropriate for all vm issues:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by IanB2 on 2008-05-29
Thanks for your help.
I've switched to using virtualbox and have found it easier to configure and more stable than VMWare.

---


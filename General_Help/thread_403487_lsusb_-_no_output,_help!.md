---
title: "lsusb - no output, help!"
date: 2007-04-07
forum: General Help
---

### Post by Victor.Barna on 2007-04-07
sudo lsusb gives me absoltely nothing:

slack@slack-desktop:~$ sudo lsusb
slack@slack-desktop:~$ 

what could be wrong?i am using a standard ubuntu 6.10 install, all upgrades done.

---

### Post by heimo on 2007-04-07
How about
```
lsmod | grep usb
```

---

### Post by kostkon on 2007-04-07
Try to do it without *sudo*:

```
~$ lsusb
```

---

### Post by Victor.Barna on 2007-04-07
same output - nothing
slack@slack-desktop:~$ lsusb
slack@slack-desktop:~$ lsmod | grep usb
slack@slack-desktop:~$ 

it looks like the ubuntu installation hasn't detected my usb ports.
if i run dmesg , i can't find anything about the usb port in the listing.

What can i do? reinstall?

---

### Post by heimo on 2007-04-07
What happens if you run:
```

sudo modprobe ehci_hcd uhci_hcd 
```
and perhaps
```
sudo /etc/init.d/udev restart
```

and then check lsusb / lsmod | grep usb?

---

### Post by Victor.Barna on 2007-04-07
```

slack@slack-desktop:~$ sudo modprobe ehci_hcd uhci_hcd
FATAL: Error inserting ehci_hcd (/lib/modules/2.6.20-14-generic/kernel/drivers/usb/host/ehci-hcd.ko): Unknown symbol in module, or unknown parameter (see dmesg)


```

and

```

slack@slack-desktop:~$ sudo /etc/init.d/udev restart
 * Loading additional hardware drivers...                                [ OK ] 
slack@slack-desktop:~$ 


```

---

### Post by heimo on 2007-04-07
If you have older kernels installed, try booting to one of those and see if there's difference. Check your /var/log/messages and "dmesg | less" for any errors about USB.

---

### Post by Victor.Barna on 2007-04-07
All that i can get about usb is this:

```
[26732.992000] usbcore: registered new interface driver usbfs
[26732.996000] usbcore: registered new interface driver hub
[26732.996000] usbcore: registered new device driver usb

```

i tried using 2.6.17 2.6.18 and 2.6.20 kernels.Nothing...I'm going to check the motherboard for blown capacitors ect..

---

### Post by Victor.Barna on 2007-04-07
ok guys, i'm sorry for the trouble, the usb ports were just disabled in bios(i restored fail safe defaults in bios a couple of days ago because of a hard-drive issue and i forgot to turn on the usb ports ) :lolflag: 

thanks for the replies!
vic.

---

### Post by heimo on 2007-04-07
Hey! No problem, happy to hear that it wasn't hardware problem or problem in Ubuntu. :)

---


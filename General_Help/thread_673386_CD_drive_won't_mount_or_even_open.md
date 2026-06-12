---
title: "CD drive won't mount or even open"
date: 2008-01-20
forum: General Help
---

### Post by Salza on 2008-01-20
Hi all!

I'm fairly new to Ubuntu.  I've installed it onto my computer a few weeks ago and I love it!

Ok, to the problem.  As the title suggests, my cd drive won't doesn't work.  It was opening, closing and mounting cds this morning, but now it won't open nor acknowledge that there's anything in there (a cd is stuck in there).

When I try to eject I get an error: [COLOR="Sienna"]eject: unable to find or open device for: `/dev/hdc'[/COLOR].

I've read the other post " unable to mount selected volume (my cd drive won't mount)" but figured I'd start a new post because the drive wouldn't even open or read the cd.

When I try [COLOR="Sienna"]dmesg | grep CD[/COLOR] in terminal I get nothing.

```
dmesg | grep cd
[    0.000000] Kernel command line: root=UUID=a1d6367f-1435-478b-a240-cc6fdd20cd31 ro quiet splash
[   28.794425] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   28.794620] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   28.794654] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000d000
[   28.896259] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   28.896290] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   28.896316] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000d400
[   29.000246] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   29.000283] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   29.000308] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000d800
[   29.106266] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   29.106326] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   29.106387] ehci_hcd 0000:00:10.3: irq 16, io mem 0xe7000000
[   29.106394] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.940000] usb 3-1: new low speed USB device using uhci_hcd and address 2
```


```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a1d6367f-1435-478b-a240-cc6fdd20cd31 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4f23bc50-28eb-47b3-b78e-987207f6ad2f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Thanks in advance for any help!

---

### Post by danwood76 on 2008-01-20
If you reboot the PC are you able to open the CD drive before the OS loads by pressing the eject button?
If not then you drive may be dead or the power to it came loose.

regards,
Danny

---

### Post by Salza on 2008-01-20
Ok, I turned off my computer, and opened it up.  Everything seemed to be fine, but I unplugged and plugged back in, and now it works just fine!

Thanks!

---


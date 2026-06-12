---
title: "PCTV hybrid stick"
date: 2007-02-25
forum: General Help
---

### Post by chrroessner on 2007-02-25
Hi,

I founf this howto for edgy:

[http://wiki.ubuntuusers.de/em28xx](http://wiki.ubuntuusers.de/em28xx) and tried to get my Dazzle Hybrid Stick USB to work.

```

Bus 003 Device 006: ID eb1a:2881 eMPIA Technology, Inc.

```

I downloaded the firmware_v3.tgz and unpacked it under /lib/firmware

Edgy itself seems already to have the em28xx module. I tried to find the mercurial stuff, but as I could not find it and it already seems to be in ubuntu kernel, I hoped to get it done by modprobe em28xx

```

[  226.352000] usbcore: registered new interface driver em28xx
[  489.112000] usb 3-8.2: USB disconnect, address 3
[ 5837.360000] usb 3-8.2: new high speed USB device using ehci_hcd and address 6
[ 5837.452000] usb 3-8.2: configuration #1 chosen from 1 choice

```

But where is /dev/video0?

So, please, could someone give me a short hint where to find answers?

Thanks
Christian

---

### Post by chrroessner on 2007-02-27
*bump*

---

### Post by chrroessner on 2007-03-04
Is there really nobody, who might have any idea on that? :-(

---

### Post by Chal on 2007-03-21
i have the same probl and dmesg messages as you

i cannot find my /dev/video  or /dev/video0

and i have the dazzle tv stick   (pctv 71e)

is anyone out there who can help us please?

thx

---

### Post by tomplast on 2007-06-20
I also have this problem :(

---

### Post by mulvila on 2007-07-02
I am not sure if this is usefull or your particular chip, but getting the latest em28xx module could help
[http://mcentral.de/wiki/index.php/Em2880](http://mcentral.de/wiki/index.php/Em2880)

I am making prggress with em 2860

---

### Post by TpyKv on 2008-04-15
I hope you find a solution to this!! Good luck, my stick has not been used since using Ubuntu....

---

### Post by TpyKv on 2008-04-29
Bump!

:lolflag:

Just in case anyone is any wiser by now??

---


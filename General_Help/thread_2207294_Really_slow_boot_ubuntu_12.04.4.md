---
title: "Really slow boot ubuntu 12.04.4"
date: 2014-02-23
forum: General Help
---

### Post by cuentaparalinux on 2014-02-23
Dear users,

I'll write it briefly: Made a ubuntu 12.04 fresh install dual boot with w7, everything went ok. At first it booted quickly, but now it seems every day it keeps booting slower. I have researched a bit and installed bootchart, but can't manage to know what the problem is. I have a laptop with 4gb ram and I5 processor.

I attached the bootchart image log. Hope you can help me. Thanks in advance and regards.

Edit: it is impossible to read the attached image, so here it is [http://i.imgur.com/59E6bmk.png](http://i.imgur.com/59E6bmk.png)

---

### Post by papibe on 2014-02-23
Hi cuentaparalinux.

Any nfs or samba mount?

Could you post these files after a fresh boot?
```
/var/log/boot
/var/log/dmesg

```
Please paste the files here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and then post back the links to them.

Regards.

---

### Post by cuentaparalinux on 2014-02-23
Hi papibe

I don't have any nfs or samba mount (in fact I had to search what were them).

Here is boot log: [http://paste.ubuntu.com/6980158/](http://paste.ubuntu.com/6980158/)

and dmesg: [http://paste.ubuntu.com/6980143/](http://paste.ubuntu.com/6980143/)

Thanks a lot for your answer! Best regards.

---

### Post by papibe on 2014-02-23
Thanks.

It looks like udev is taking a long time to load all devices (+16 secs):
```
[    7.257251] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   24.234616] udevd[735]: starting version 175
```
Could you post the content of this file:
```
/etc/fstab
```
And also, could you open a terminal, run this command and post back its results?
```
udevadm trigger -v
```
Regards.

---

### Post by cuentaparalinux on 2014-02-23
Hi papibe

Here is fstab: [http://paste.ubuntu.com/6983273/](http://paste.ubuntu.com/6983273/)

and udevadm trigger -v: [http://paste.ubuntu.com/6983277/](http://paste.ubuntu.com/6983277/)
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]Thanks a lot for your help and time. Kind Regards.

---

### Post by cuentaparalinux on 2014-02-24
Bump

Don't leave me please.

---

### Post by papibe on 2014-02-25
Perdon por la tardanza.

Try this:
```
sudo apt-get purge ureadahead

sudo apt-get udpate

sudo apt-get install ureadahead
```
Then restart.

If that does not help. Please post the content of this file:
```
/var/log/udev
```
Let us know how it goes.
Regards.

---

### Post by cuentaparalinux on 2014-02-25
Hi Papibe,

Unfortunately nothing has changed. Ureadhead didn't help.

Here is /var/log/udev: [http://paste.ubuntu.com/6992926/](http://paste.ubuntu.com/6992926/)

Thanks a lot for your help (Muchas gracias!!). Regards!

---

### Post by cuentaparalinux on 2014-03-01
Bump

¿Could you please suggest anything else? Regards

---


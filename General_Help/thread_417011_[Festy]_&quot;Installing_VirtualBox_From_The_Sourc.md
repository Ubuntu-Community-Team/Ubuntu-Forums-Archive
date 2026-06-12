---
title: "[Festy] &quot;Installing VirtualBox From The Sources&quot; (`/dev/vboxdrv': No such file or di)"
date: 2007-04-21
forum: General Help
---

### Post by derbouka on 2007-04-21
Hi!

I'v followed the tutorial "2 Installing VirtualBox From The Sources" from [http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu) but in the step:
```
chmod 660 /dev/vboxdrv
```
I receive this:
```
chmod: cannot access `/dev/vboxdrv': No such file or directory
```
I've actually searched for the file `/dev/vboxdrv' but it really don't exist..

Does anyone know how to solve this?

Best regards

---

### Post by derbouka on 2007-04-21
By the way, I'v run the command 
```
sudo /etc/init.d/vboxdrv setup
``` and I had this output:
```
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 ^T                                                                       [ OK ]
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
```
maybe is something wrong with my kernel.. I'm using the version: 2.6.20-15-386

---

### Post by joff13 on 2007-04-26
HI,

I got the same problem after upgrading ubuntu to festy

---


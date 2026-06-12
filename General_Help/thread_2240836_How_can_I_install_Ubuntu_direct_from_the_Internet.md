---
title: "How can I install Ubuntu direct from the Internet?"
date: 2014-08-22
forum: General Help
---

### Post by Jonatan Formentera on 2014-08-22
Hi, I have a netbook with Ubuntu 12.04. It works ver slowly. I think it's because I made a mistake and installed a version with 64 bits. I l'd like to install a version with 32. I've made a usb pen bootable and tried to install it, but the BIOS doesn't read it. When I installed Ubuntu a time ago, it happened the same, but I installed it with the wubi installor direct from the Internet working on the windows side. I looked at the Ubuntu Website but I'm a little lost. I can find something similar or perhaps it has another name. Can anyone tell me if there  still is such a possibility?
Thanks

---

### Post by chandowd on 2014-08-22
Did you check here:[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) ?

---

### Post by Jonatan Formentera on 2014-08-22
Yes. I checked there.I've looked for information on the Internet and I've discovered I can use the bootabled ISO image as a wubi.exe from the Windows platform. I'm going to test it.
I' tell you.
thanks

---

### Post by Impavidus on 2014-08-22
Normally the 64 bit version should be faster than 32 bit, provided your processor supports it. If it doesn't, it won't boot at all. So your processor supports 64 bit (as do most processors nowadays). Only in the rare case where you have enough memory for 32 bit but not for 64 bit the 32 bit version may be faster.

Wubi is obsolete. The only way to install Ubuntu is from a bootable disk/usb.

What are the specs of your system?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Jonatan Formentera on 2014-08-22
The process is so. (It's in Spanish but by the images you can understand it): [http://www.forinformatica.com/2013/07/como-instalar-ubuntu-usando-wubi/](http://www.forinformatica.com/2013/07/como-instalar-ubuntu-usando-wubi/) . You can install Ubuntu from the windows platform without being in need of the Internet

---

### Post by Jonatan Formentera on 2014-08-22
Specs:
CPU: 1.6 GHz. 1MB L2 cache
Memory: 1 GB DDR 3 memory
Storage 320 GB HDD

---

### Post by ajgreeny on 2014-08-22
I suggest you use another *ubuntu version rather than the standard Ubuntu with unity, as your system specs are not really up to unity running as fast as you probably want it to. Xubuntu or Lubuntu would be much quicker than Ubuntu, I think.

I also strongly recommend that you forget about using wubi as it is no longer supported and you will get very little help from anyone here should things go wrong with it, mainly because no-one here uses it or know much about it any more.

If you wish you can get the [minimum install CD version]("https://help.ubuntu.com/community/Installation/MinimalCD"), and boot to that, then install xubuntu-desktop, which will get you to the exact same position as if you downloaded the xubuntu iso file, installed it, and then updated it after installing.

---


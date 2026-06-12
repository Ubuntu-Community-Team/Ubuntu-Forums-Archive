---
title: "How to install Ubuntu 12.04 on a Chromebook?"
date: 2014-02-08
forum: General Help
---

### Post by carmen2012 on 2014-02-08
I'm thinking of buying a Chromebook and installing Ubuntu 12.04 on it.  I know there are a lot of tutorials that detail this process using Crouton.

However, is there any way to install Ubuntu on a Chromebook without having to use a third party utility?  I would really prefer to just install Ubuntu on it like you would on a desktop or a laptop.

Thank you

---

### Post by carmen2012 on 2014-02-10
Anyone?

---

### Post by sandyd on 2014-02-10
lifehacker has a nice guide
[http://lifehacker.com/how-to-install-linux-on-a-chromebook-and-unlock-its-ful-509039343](http://lifehacker.com/how-to-install-linux-on-a-chromebook-and-unlock-its-ful-509039343)

---

### Post by carmen2012 on 2014-02-10
Hi Sandyd

Thanks for your response.  I have seen this LifeHacker guide as well as a couple of others.  This one does make use of the Crouton script.  I was wondering was if there was a means of installing Ubuntu 12.04 on a Chromebook without the need of a third party script like Crouton.

Thank you

---

### Post by IPvFletch on 2014-02-10
I often install Ubuntu or other flavors using PXE boot to a TFTP server and use pxelinux.0 as the nvram so it loads. Then it begins the Ubuntu installation and it installs over the Internet from a mirror. It looks like some Chromebooks support PXE boot, you could try that.. at least to see if PXEboot will load you load an nvram kernel and initrd via TFTP. From there anything should be possible. Writing to disk will be scary, I mean cuz you will lose your ChromeOS. I have ChromeOS on a bootable thumbdrive though, just in case I ever need it.  :)

---


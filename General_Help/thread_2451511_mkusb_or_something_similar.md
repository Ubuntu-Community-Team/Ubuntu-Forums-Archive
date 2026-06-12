---
title: "mkusb or something similar?"
date: 2020-10-05
forum: General Help
---

### Post by Autodave on 2020-10-05
Looking for mkusb and I noticed that it is available a few different ways now?  I really can't remember the last time that I used it, but I don't remember how I installed it.  Is mkusb still the best choice or is there something better now?  I need to create a bootable USB to install Xubuntu 20.04 on a new machine at church.

Thanks in advance!

---

### Post by SeijiSensei on 2020-10-05
You probably want to try the usb-creator-gtk package. There's also a usb-creator-kde package for Kubuntu.

---

### Post by tea for one on 2020-10-05
Here is the web page with ppa info.

It's a good choice for making [COLOR="#0000FF"]live[/COLOR] usb devices. 

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by C.S.Cameron on 2020-10-06
```
sudo add-apt-repository universe
sudo add-apt-repository ppa:mkusb/ppa
sudo apt update
sudo apt install mkusb
sudo apt install usb-pack-efi   
```

I think mkusb is the best USB maker.

---


---
title: "Can't get ATI 3D enabled"
date: 2006-10-10
forum: General Help
---

### Post by bogey on 2006-10-10
I have an ATI 9800 Pro video card and I am trying to get 3D acceleration working.

Following the Ubuntu documentation I checked to see if it was working, and it is not.

don@don-desktop:~$ glxinfo | grep rendering
direct rendering: No

So next I followed the 3D ATI Video Driver documentation:
- Checked Synaptic and found that xorg-driver-fglrx was already installed
- Next I ran "sudo dpkg-reconfigure xserver-xorg", selected the fglrx driver, followed the rest of the instructions, and rebooted my computer.

So I checked again to see if it was enabled and it still says that it is not.  I have done this a couple of times with the same result.

Any advice on how to enable it?

---

### Post by PriceChild on 2006-10-10
From: [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

[SIZE=-1]```
sudo apt-get install linux-restricted-modules-$(uname -r)
```You may wanna check you've done this before reconfiguring X
[/SIZE]

---

### Post by bogey on 2006-10-10
Yes that worked. 3D is not enabled.

Thanks!!!

---

### Post by bogey on 2006-10-10
Sorry, typo. 3D is now enabled.

---

### Post by PriceChild on 2006-10-10
No problem :)

---


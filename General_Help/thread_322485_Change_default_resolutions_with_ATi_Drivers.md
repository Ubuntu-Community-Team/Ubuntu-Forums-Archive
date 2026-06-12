---
title: "Change default resolutions with ATi Drivers"
date: 2006-12-20
forum: General Help
---

### Post by alex.de on 2006-12-20
Hi, on my Windows machine I use the Omega Ati drivers for my video card because my monitor format (1440x900) is not supported with the ATi Drivers from the official website. On Linux, the Omega drivers are not supported. So I have to use the ATi ones. But, again, I can't set the resolution to 1440x900.

I was wondering, is there a way to change the video resolution of the default ATi Drivers? Like editing a file?

I know what you're saying: "Just edit the xorg.conf file". But I tryed that and it doesn't work, AT ALL.

Help would really be appreciated. Thanks.

---

### Post by Dubbayoo on 2006-12-20
sudo dpkg-reconfigure xserver-xorg

---

### Post by alex.de on 2006-12-20
Well, I don't know the good choice of half of these answers. When it asks me to enter the resolutions I want to use, I add a star to it but still no changes, even after a reboot.

---


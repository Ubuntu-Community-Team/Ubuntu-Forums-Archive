---
title: "Is there a way to save an Ubuntu config to USB?"
date: 2006-12-21
forum: General Help
---

### Post by arrow_runner on 2006-12-21
I have a laptop w/ a dead hard drive.](*,) 

I'd like to be able to save my network/application configurations to USB thumb drive, and have ubuntu use that config while it loads live from cd.

I know this is possible w/ knoppix and dsl, but the version of knoppix and dsl able to run on my laptop are either too slow or don't have enough apps to do what I want/need.

Is there a how to on this with ubuntu? I've searched and searched, but have found nothing.

Thanks.

---

### Post by darrenm on 2006-12-21
The only way I know to is on a per-user basis.

basically back up your /home/$USERNAME directory then copy it back over afterwards. All the app settings are in /home/$USERNAME/.something

---

### Post by yopnono on 2006-12-21
A tip remove the cache from .mozilla folder and remove the .thumbnails = it's only taking up space on you usb device.

---

### Post by lamego on 2006-12-21
Maybe you are looking for this ?
[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

---

### Post by arrow_runner on 2006-12-21
Perfect, I'll try it when I get home after Christmas, thank!

---


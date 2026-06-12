---
title: "Failed Update and Error Message"
date: 2018-11-07
forum: General Help
---

### Post by daniell59 on 2018-11-07
The latest update failed and now all I get are error messages. Is there any way of fixing this? Also, how can I recover some of the files?

Ubuntu 16.04 64

---

### Post by hiec2 on 2018-11-07
You could boot from an installation medium (CD, USB stick). Just make sure the installation medium supports a live session (the alternate installer doesn't). There you can try to mount your Lubuntu partitition as read-only and backup your files. If that does not work you could try to run a file system check as suggested in the error message you posted, but I do not know if that could result in data loss, so please be careful.

---

### Post by daniell59 on 2018-11-07
> **hiec2 said:**
> You could boot from an installation medium (CD, USB stick). Just make sure the installation medium supports a live session (the alternate installer doesn't). There you can try to mount your Lubuntu partitition as read-only and backup your files. If that does not work you could try to run a file system check as suggested in the error message you posted, but I do not know if that could result in data loss, so please be careful.

I was able to copy the files that I wanted to. Do you have any idea what happened to crash my Ubuntu 16.04. I will just reinstall it to 18.04. I have dealing with two old computers. I wonder if I would be better off with a lighter version.

---

### Post by hiec2 on 2018-11-07
Sorry, I have no idea what happened. You could check the SMART data of your disks, for example with the Disks system utility or with smartmontools on the console. Maybe your harddisk is dying.

Lubuntu is pretty lightweight. I use it for about 15 year old hardware myself. With that being said I was looking into even lighter distros myself recently. The two most interesting to me were Bodhi Linux Legacy, an Ubuntu derivative, and BunsenLabs Helium, which is based on Debian, like Ubuntu. Check them out :-)
[http://www.bodhilinux.com/w/selecting-the-correct-iso-image/](http://www.bodhilinux.com/w/selecting-the-correct-iso-image/)
[https://www.bunsenlabs.org/](https://www.bunsenlabs.org/)

---


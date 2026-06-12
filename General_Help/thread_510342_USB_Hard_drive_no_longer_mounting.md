---
title: "USB Hard drive no longer mounting"
date: 2007-07-26
forum: General Help
---

### Post by zaxor0 on 2007-07-26
I have a USB Hard drive that used to mount. It is NTFS and was read only, so I wanted it to be read write. I used the command "chmod 666 -v /media/FANTOM" fantom being the usb hard drive. This did not work so I did some research and I got ntfs configuration tool. When I run it it just gives me the option to check the ability to write. I was never able to select any mount points or anything. Normally the hard drive would always mount automatically, but after doing all of this and rebooting it no longer works. I can see the hard drive in the "Computer" folder but when I right click it and then click mount i get an error message about it being unmountable. There is a log for it but I tried to follow the steps but nothing seems to work.

I have tried to use the hard drive on a different computer with Ubuntu and it works fine.

What should I do to make it mount?

Here is the related section of /etc/fstab:

Entry for /dev/sda1 :
UUID=c2cba310-758f-4504-96ab-296750df40b4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=c8dc6bf5-ff0a-4acd-ae76-05c2d50e0b8e none swap sw 0 0

---


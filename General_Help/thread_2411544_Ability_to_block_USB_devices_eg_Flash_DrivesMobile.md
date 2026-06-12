---
title: "Ability to block USB devices eg Flash Drives/Mobile phones"
date: 2019-01-31
forum: General Help
---

### Post by davidallay on 2019-01-31
I'm wondering if anyone can point me in the right direction. I'm pretty new to Linux so would need this explaining to me.

I have tried a few different ways to block usb devices (below) however, they just do not seem to work. I'm using a Lubuntu image and it is going to be used in an office where we prohibit the use of usb Flash Drives etc due to Data Protection. So the only way we would be able to use it is if we re-enable it via the Administrator account.

[https://www.tecmint.com/block-usb-storage-devices-in-linux/](https://www.tecmint.com/block-usb-storage-devices-in-linux/)
[https://askubuntu.com/questions/153964/how-do-i-prevent-standard-users-from-using-the-usb-ports](https://askubuntu.com/questions/153964/how-do-i-prevent-standard-users-from-using-the-usb-ports)


**Any help would be appreciated!**

---

### Post by HermanAB on 2019-01-31
TIMTOWTDI - To block al removable devices I would try to put a spanner in the works, so that nothing can mount on /media.  One way could-be to delete /media and make a file with the name media and make it immutable.

---

### Post by SeijiSensei on 2019-01-31
Epoxy in the USB ports is the best solution.

You can disable the usb-storage module.  See [https://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/](https://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/) or other sources on the Internet for how to do this.

In [https://www.tecmint.com/block-usb-storage-devices-in-linux/](https://www.tecmint.com/block-usb-storage-devices-in-linux/) they suggest renaming the kernel module.  Did you try that, and it didn't work?

Did you trying removing the module from the running kernel with "sudo rmmod usb-storage"?  If you run "lsmod | grep usb" do you see the module listed?

```
lsmod | grep usb
usb_storage            49361  1 

```

---


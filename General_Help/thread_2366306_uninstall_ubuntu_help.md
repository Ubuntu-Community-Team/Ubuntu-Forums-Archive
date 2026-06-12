---
title: "uninstall ubuntu help"
date: 2017-07-16
forum: General Help
---

### Post by techsupport-hotmail on 2017-07-16
hi all. im having a new notebook in next few days and i need to uninstall ubuntu on this current xp notebook and place another os on for sale but im unable to uninstall it.
ive gone into bios to change boot settings but it wont let me do that to boot from usb and i got ubuntu on a single boot and not a dual boot. 
any ideas?
thanks.

---

### Post by ajgreeny on 2017-07-16
You may need to hold a specific key when you power-on the machine to get to the boot boot menu, on an old netbook I still use with Lubuntu it is F11, so try all possible candidates and you may find the correct key.

If you still have the written manual for the machine that should also tell you or you can search the web for the way to do it on that machine model.

Once you get the USB booted you do not need to uninstall whatever is on the machine; just install over it.

---

### Post by yancek on 2017-07-16
You should see a message on screen immediately after booting telling you which key to use to enter BIOS/Setup.  Have you ever booted from a usb with this computer  If you don't have an option to boot from usb, it may be that the computer is not capable ofbooting from usb as was the case years ago when xp was first released.  Using a CD/DVD might then be your only option.

---

### Post by techsupport-hotmail on 2017-07-16
i can get into the bios but when i go to change it to boot from usb it still wants to boot from hdd. is there a way that i can wipe ubuntu before then installing new os. i did download ubuntu again onto a memory stick as a iso but still wont work on here???

---

### Post by yancek on 2017-07-16
You should be able to boot the system you want to install from a CD/DVD and just intall overwriting everything including the MBR currently on it.  What are you planning to install?  If it is some version of windows, that's the default, overwrite everything.  You don't "uninstall" operating systems the way you do applications, you simply format and overwrite the current partition.  I asked in my previous post if you had ever booted a usb from this computer, might not have the capability.

>  i did download ubuntu again onto a memory stick as a iso but still wont work on here??? 		

I don't know what that means.  You can't just download an iso to a flash drive or copy it to a flash drive.  You need to use specific software to create a bootable usb.

---

### Post by oldos2er on 2017-07-16
I think yancek is correct by suggesting the USB stick may be the problem. How did you create it and have you tested it on a different computer?

[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

---


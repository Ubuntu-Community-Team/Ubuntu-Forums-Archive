---
title: "How to install Chromium OS with .img...NOT .iso?"
date: 2014-10-28
forum: General Help
---

### Post by Mike_Walsh on 2014-10-28
Evening, all.

Need a wee bit of advice from some of our installation experts.

I'm trying to install one of Hexxeh's 'Vanilla' Chromium OS builds to a USB flash drive.. I've downloaded the zip file, and extracted the file inside, which is an .img file, NOT an .iso file.

Hexxeh's instructions say to install the .img file to the USB drive via the 'dd' command, like this:-

```
dd if=ChromeOS.img of=/dev/sdX bs=4M
```

where 'ChromeOS.img' is the path to the file, and '/dev/sdX' is the path to the USB drive. I can get the second path, no problem, but I'm hanged if I can get the syntax, or content, for the first path. How do I actually write this?

To help, my details are as follows:-

1) My user name is 'paul';
2) The .img file is in home/Downloads/ChromeOS (ChromeOS is a folder I've created specially for this task);
3) the file name is 'ChromeOS-Vanilla-4028.0.2013_04_20_1810-r706c4144.img'

All the blogs I can find say to install this from Windows, using something called 'Windows DiskWriter'. Well, I no longer have Windows in the house, so that's out. Where they DO mention doing it in Ubuntu, they say to use 'usb-imagewriter'. It appears this no longer exists, and has become 'Startup Disk Creator', which I DO have. However, every time I try to use this, it does one of two things.

1) It asks for an .iso file, NOT an .img one.
2) Furthermore, it keeps saying it can't find the file! I wonder if this has anything to do with the fact that I'm sharing my /home partition with my Lubuntu install?

Any advice would be appreciated. Remember, please, that what I actually need help with, at this point, is the syntax & content of the first path for the 'dd' command; in other words, how do I actually enter this in the terminal?

If necessary, I can move the folder to a location where I KNOW it will be found.

Regards,

Mike.

---

### Post by yancek on 2014-10-28
Open a terminal and change to your ChromeOS directory where you have the .img file and run the following command.  Hope you don't have anything on the flash drive you want to keep and make sure you get the correct X device.  Don't know if this works with .img files, never use them as I understand they are generally used only on window?

> dd if=ChromeOS-Vanilla-4028.0.2013_04_20_1810-r706c4144.img of=/dev/sdaX


---

### Post by Mike_Walsh on 2014-10-28
Hi, yancek.

Thanks for the reply! I wondered about that myself; unless Hexxeh's under the impression that this will only ever be tried by Windows users, and not those who are already Linux converts...

My terminal skills are steadily improving; I no longer copy & paste everything. I type stuff in now, and I must get it right, since 99 times out of 100 my commands are executed. I am, however, aware that whatever language Ubuntu is written in, if you so much as get a dot, or a dash, or a comma, or a space, or a bracket, or quotation mark in the WRONG place, it CAN have disastrous consequences; although I realise the terminal will usually warn you if you're about to try and do something REALLY stupid!

I'm probably in exactly the same place on the 'learning curve' as most folk are, 6 months down the line...

Sorry for a 'noob' question now; when you say 'open a terminal AND CHANGE TO YOUR CHROMEOS DIRECTORY....how do I do that from the terminal? This is EXACTLY what I mean about not knowing content and/or syntax for this stuff yet!

Regards,

Mike.

---


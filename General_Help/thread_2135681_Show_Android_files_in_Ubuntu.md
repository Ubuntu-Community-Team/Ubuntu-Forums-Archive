---
title: "Show Android files in Ubuntu"
date: 2013-04-15
forum: General Help
---

### Post by WUTANG4EVER on 2013-04-15
I am new to ubuntu and love it. I will never will go back to windows. Well I can not seem to figure out how to get my samsung phone to show up in my home file under devices or in disk utility. the drivers do show up when i enter lsusb. I also have a laptop with ubuntu and last night i downloaded something i dont remember but the files from phone did show up in home folder but the laptop crashed and ubuntu would not boot back up. Im not worried about the laptop but does anyone no how i can get my androids files to show up on my home folder. Also the file system is vfat on android and im running ubuntu 12.04 on a 32 bit system. Thanks

---

### Post by dargaud on 2013-04-15
Hello, normally the phones connect with the MTP protocol, but Linux support for it is spotty to say the least. Some people have gotten it to work but I use a different method: simple Mass Storage connection. You didn't specify which phone you have, so I'll give you indications for the Galaxy SII.
- do not connect phone
- [Settings]
- [More...]
- [USB Utilities]
- [Connect storage to PC]
- connect cable
- [Turn on USB storage]
- [OK]
- then click on the notification icon on your PC to mount it.

Remember to eject/unmount from the PC before you press [Turn off USB storage] on the phone, otherwise the last files you copies may not sync.

---

### Post by WUTANG4EVER on 2013-04-15
Ya i figured it out. I had to have, mount usb checked off and also usb debugging checked off to. On windows you only check off usb mount. Kinda weird but worked. Thanks any ways.

---

### Post by Memphis88 on 2013-04-15
Hey, 

I'm new like you and I found the AirDroid app is nice to use - wrote a little guide:

[http://memphiscodingadventures.wordpress.com/2013/04/15/the-magic-of-airdroid-ubuntu-12-10/](http://memphiscodingadventures.wordpress.com/2013/04/15/the-magic-of-airdroid-ubuntu-12-10/)

I have been having issues connecting my phone to my PC as a USB Mass-Storage Device...if there's a quick fix I'd love to hear it so using AirDroid for now.

Thanks :)

---

### Post by Mark Phelps on 2013-04-15
> **Memphis88 said:**
> Hey, 

I'm new like you and I found the AirDroid app is nice to use - wrote a little guide:

[http://memphiscodingadventures.wordpress.com/2013/04/15/the-magic-of-airdroid-ubuntu-12-10/](http://memphiscodingadventures.wordpress.com/2013/04/15/the-magic-of-airdroid-ubuntu-12-10/)

I have been having issues connecting my phone to my PC as a USB Mass-Storage Device...if there's a quick fix I'd love to hear it so using AirDroid for now.

Thanks :)

If your phone is one of the newer ones using either ICS or Jelly Bean, then you won't have the USB Utilities option mentioned here, nor will you have the Mass Storage option -- Those were removed from those newer versions of Android.

---

### Post by Memphis88 on 2013-04-15
Thanks very much, luckily I managed to get mine working and am not running ICS or Jelly Bean, but I'll update my notes.

---


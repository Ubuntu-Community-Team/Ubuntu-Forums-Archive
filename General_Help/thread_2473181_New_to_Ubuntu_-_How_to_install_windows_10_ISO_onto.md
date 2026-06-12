---
title: "New to Ubuntu - How to install windows 10 ISO onto USB key?"
date: 2022-03-26
forum: General Help
---

### Post by 82eridani on 2022-03-26
In a bind, long story but trying to use ubuntu to get the windows 10 iso onto a usb key. I read that woeusb works... but I cannot figure out how to install it and I cannot find a package manager in ubuntu like Synaptic..I don't know what anything is called or how to invoke things well...I don't plan on keeping ubuntu, I just need it to perform this one operation.

For a total noob...what is the easier, quickest way to correctly get he windows ISO installed onto a USB key?

---

### Post by demonenero84 on 2022-03-26
I have just spent a few hours cursing for a similar problem ( My dad wanted me to install win7 on an old pc). Long story short I used rufus on a win 10 pc ( actually it is just my pc booting from a different hard disk )
 Try to take a look here
[https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu](https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu)
best of luck mate

---

### Post by DuckHook on 2022-03-26
> **demonenero84 said:**
> I just spent a few hours cursing for a similar problem ( My dad wanted me to install win7 on an old pc). Long story short I used rufus on a win 10 pc ( actually it is just my pc booting from a different hard disk )
 Try to take a look here
[https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu](https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu)
best of luck mate
Thanks for this contribution. I didn't know such a tool existed and I usually stay relatively up to date with Joey's bloggings.

---

### Post by demonenero84 on 2022-03-26
You are welcome, I tried balenaEtcher before using rufus and it warned me to use woeusb :lolflag:

---

### Post by bobunderwood99 on 2022-03-26
Hello,

Try Ventoy.

[http://www.ventoy.net/en/index.html](http://www.ventoy.net/en/index.html)

---

### Post by C.S.Cameron on 2022-03-27
I could never get WoeUSB to work.
You can install Windows using Ubuntu's GRUB/UEFI:
[https://askubuntu.com/questions/1337487/using-ubuntu-to-reinstall-windows-10-using-grub2-and-no-usb](https://askubuntu.com/questions/1337487/using-ubuntu-to-reinstall-windows-10-using-grub2-and-no-usb)
Mkusb also does a good job of installing Windows:
[https://askubuntu.com/a/1274975/43926](https://askubuntu.com/a/1274975/43926)

---

### Post by timgood on 2022-03-30
> **bobunderwood99 said:**
> Hello,

Try Ventoy.

[http://www.ventoy.net/en/index.html](http://www.ventoy.net/en/index.html)

Absolutely agree. Ventoy is brilliant. Installing to USB is easy - there is a graphical as well as a browser-based install. Once installed you can simply drag bootable ISO files into it and it will list them so you can select which to boot. I have Windows 10, 11, Hiren's Boot CD and 3 Linux distros on one key. Fabulous bit of kit.

---


---
title: "UNetbootin Install"
date: 2017-10-29
forum: General Help
---

### Post by sublimelife89 on 2017-10-29
I'm trying to install lubuntu 17.10 on an old desktop of mine using unetbootin on a flash card and I keep getting this error when I try to install.    
 
[ end Kernel panic - not syncing: IO -APIC + timer doesn't work! Boot with apic=debug and send report. Then try booting with the 'naopic' option.  


Can anyone tell me what this means??

---

### Post by sudodus on 2017-10-29
Did you try to boot with the boot option **apic=debug** and send a bug report and after that try to boot with **noapic**?

That is what the programmer suggests.

See this link: [BootOptions](https://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

[hr][/hr]
If still no luck, please check with md5sum, that the downloaded iso file is good,

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If still no luck, and you are running linux, I suggest that you try with another tool, for example mkusb according to this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

Otherwise, if you are running Windows, I suggest that you try with Rufus,

[https://rufus.akeo.ie/](https://rufus.akeo.ie/)

---

### Post by HermanAB on 2017-10-29
Hmm, note that you don't need any special tools like unetbootin or mkusb and the like.

You can copy the ISO file to the memory stick with dd or even cat, which all versions of Linux have by default.

---


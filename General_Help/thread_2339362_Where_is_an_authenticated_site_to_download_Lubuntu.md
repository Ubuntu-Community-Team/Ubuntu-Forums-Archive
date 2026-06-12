---
title: "Where is an authenticated site to download Lubuntu?"
date: 2016-10-07
forum: General Help
---

### Post by AbleTassie on 2016-10-07
Thanks,

A.

---

### Post by Bashing-om on 2016-10-07
AbleTassie; Hello;

In your posting , the above quick links in "Ubuntu Community" :
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]works a treat
[/INDENT][/INDENT]

---

### Post by vasa1 on 2016-10-07
Also [http://lubuntu.me/](http://lubuntu.me/)

---

### Post by sgage on 2016-10-07
> **AbleTassie said:**
> Thanks,

A.

I always get my installation images at [cdimage.ubuntu.com]("http://cdimage.ubuntu.com"). All the flavors are there, including Lubuntu, of course.

---

### Post by AbleTassie on 2016-10-07
Thanks Bashing. I am doing this for a friend. I will transfer the downloaded Lubuntu file to a thumbdrive then boot from the usb for installation. 

Question: Can I also download Libre Office from somewhere and install Libre Office from the usb/thumbdrive after Lubuntu is installed?

Thanks,

A.

---

### Post by Bashing-om on 2016-10-07
AbleTassie; WOW ..

While you may install "libreoffice" from a USB - piggyback ; It will be a long hard road finding and installing all the myriad of dependencies !
That is what the package manager is for . Makes a lot more sense to install "libreoffice" direct with the package manager !
Get that machine to a wired internet connection and be done with it .

[INDENT][INDENT]just my thought on the matter
[/INDENT][/INDENT]

---

### Post by DuckHook on 2016-10-07
> **Bashing-om said:**
> 
[INDENT][INDENT]just my thought on the matter
[/INDENT][/INDENT]&#8230;and a marvellous thought it is&#8230;

@AbleTassie

You may wish to consider Xubuntu instead. 

It is only marginally more resource-hungry than Lubuntu but already has *libreoffice* by default.

---

### Post by AbleTassie on 2016-10-08
I am trying now to boot off the usb port a Dell Latitude e6400, but the screen just says BOOTMGR is missing. Press CTRL+Alt+Delete to restart. I can hit F12 and tell it to boot off the usb, but I get the same message. 

Anybody know what I can do?

Thanks,

A.

---

### Post by howefield on 2016-10-08
Can you tell us how you created the Live USB, what application was used ?

Also, if you haven't checksummed the downloaded iso, might be worth doing that.. assuming that it is 16.04.1 that you downloaded the MD5SUMs for the desktop images are

```
d2d7edc41ea03998e267db607f92b40d *lubuntu-16.04.1-desktop-amd64.iso
72a400913ba0ed59b88c42e5aab629e9 *lubuntu-16.04.1-desktop-i386.iso
```

Using a terminal, navigate to the folder containing the iso file and type..

```
md5sum lubuntu-16.04.1-desktop-amd64.iso 
```

and compare the MD5SUM produced to the above, change the file name to suit eg, if it is the 32 bit version.

eg,
```
hugh@yakkety-laptop:/Data/Linux/Linux Isos$  md5sum lubuntu-16.04.1-desktop-i386.iso 
72a400913ba0ed59b88c42e5aab629e9  lubuntu-16.04.1-desktop-i386.iso
hugh@yakkety-laptop:/Data/Linux/Linux Isos$
```

---

### Post by kurt18947 on 2016-10-08
> **AbleTassie said:**
> I am trying now to boot off the usb port a Dell Latitude e6400, but the screen just says BOOTMGR is missing. Press CTRL+Alt+Delete to restart. I can hit F12 and tell it to boot off the usb, but I get the same message. 

Anybody know what I can do?

Thanks,

A.

Did you just copy the lubuntu .iso file to a USB drive? Though some .iso will boot directly I think, you'll probably need to use one of the apps to create a live USB.

If creating a bootable USB using Windows:

[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

If creating a bootable USB using Ubuntu:

[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

Your procedure of selecting the boot device should work if the USB drive has a bootable image on it.

Re LibreOffice, I think lubuntu 16.04 has LibreOffice in lieu of AbiWord & Gnumeric.

---

### Post by HermanAB on 2016-10-08
The other way is to make your own mirror server and install from that.  It is very easy.

Scroll down to Ubuntu Mirror:
[http://www.aeronetworks.ca/2016/02/mirror-mirror-on-wall.html](http://www.aeronetworks.ca/2016/02/mirror-mirror-on-wall.html)

---

### Post by vasa1 on 2016-10-08
> **kurt18947 said:**
> ...
Re LibreOffice, I think lubuntu 16.04 has LibreOffice in lieu of AbiWord & Gnumeric.
Lubuntu 16.04 still has Abiword & Gnumeric. No LibreOffice.

---

### Post by kurt18947 on 2016-10-10
> **vasa1 said:**
> Lubuntu 16.04 still has Abiword & Gnumeric. No LibreOffice.

Sorry for the misinformation. I've installed LXLE - an Lubuntu spin - which has LibreOffice. I assumed the change applied to Lubuntu as well.

---

### Post by vasa1 on 2016-10-10
> **kurt18947 said:**
> Sorry for the misinformation. I've installed LXLE - an Lubuntu spin - which has LibreOffice. I assumed the change applied to Lubuntu as well.LXLE comes with quite a few more applications than Lubuntu. IIRC, LXLE went past being a CD-size distro, FWIW, pretty early on in its history.

---

### Post by shartazh on 2016-10-17
Hello!
On [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu) links for download new release 16.10 is broken.

---

### Post by howefield on 2016-10-17
> **shartazh said:**
> Hello!
On [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu) links for download new release 16.10 is broken.

File a bug.

In the meantime, follow the links from [https://www.ubuntu.com/download/ubuntu-flavours](https://www.ubuntu.com/download/ubuntu-flavours)

---

### Post by AbleTassie on 2016-10-20
> **kurt18947 said:**
> Did you just copy the lubuntu .iso file to a USB drive? Though some .iso will boot directly I think, you'll probably need to use one of the apps to create a live USB.

If creating a bootable USB using Ubuntu:

[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

Your procedure of selecting the boot device should work if the USB drive has a bootable image on it.

Re LibreOffice, I think lubuntu 16.04 has LibreOffice in lieu of AbiWord & Gnumeric.

Hello everybody. I was on the road without my PC for about 10 days so sorry I have not replied. No I did not create a live usb, so that was probably the problem with booting.

Thanks,

A.

---

### Post by AbleTassie on 2016-10-20
> **HermanAB said:**
> The other way is to make your own mirror server and install from that.  It is very easy.

Scroll down to Ubuntu Mirror:
[http://www.aeronetworks.ca/2016/02/mirror-mirror-on-wall.html](http://www.aeronetworks.ca/2016/02/mirror-mirror-on-wall.html)

Thanks Herman,

A.

---


---
title: "can 32-bit printer driver work in 64-bit?"
date: 2018-07-09
forum: General Help
---

### Post by ardouronerous on 2018-07-09
I'm currently on Lubuntu 16.04 32-bit and I will be upgrading to to Lubuntu 18.04 64-bit next year, my printer is a Canon PIXMA iP2700, however, but the driver I downloaded from the Canon website is 32-bit.

Here's a link to the driver: [https://www.canon.com.au/printers/pixma-ip2700/support](https://www.canon.com.au/printers/pixma-ip2700/support)

I've tried the driver available in the kernel, the Canon iP2700 - CUPS+Gutenprint, however, many features are lacking in that driver, like printing in draft mode for example.

I've looked all over the Internet for 64-bit driver for my printer, I cannot find one.

---

### Post by ardouronerous on 2018-07-10
Bump

---

### Post by col48 on 2018-07-10
I think you're out of luck.  Canon are not very Linux-friendly, so even the drivers they do offer don't get much enthusiastic support if a bug is found.  And I think I am right in saying that 32-bit software in a 64-bit machine would need to be wrapped up to protect it from straying - not something any program looking to initiate a print would do.

---

### Post by ardouronerous on 2018-07-13
I did some googling on running 32-bit in 64-bit Ubuntu and discovered this:

[URL="https://www.unixmen.com/enable-32-bit-support-64-bit-ubuntu-13-10-greater/"]https://www.unixmen.com/enable-32-bit-support-64-bit-ubuntu-13-10-greater/
[/URL]
```
sudo dpkg --add-architecture i386
sudo apt -get update
sudo apt-get dist-upgrade
```

Do you think this will help in running my 32-bit Canon printer in 64-bit Lubuntu 18.04?

---

### Post by kurt18947 on 2018-07-14
I'm not certain but I think Brother drivers are 32 bit so it's most likely possible. Whether Canon has made an effort to make it work would be a question. I guess you could create a temporary install, either as part of a multi-boot disk or on a second hard drive/USB flash drive. You could play around with the expendable install without risking your daily user. I don't think I'd trust a Virtual Machine for exploring hardware/firmware issues.

---

### Post by ardouronerous on 2018-07-14
Thanks for the reply.  I did some digging around, and I found these: [URL="http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-ip-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/"]http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-ip-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/
[/URL]
I checked out ppa:michael-gruz/canon-trunk via [https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk](https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk) and it seems like there is a 64-bit driver for my printer in this PPA, whether it will work in Lubuntu 18.04, I don't know, considering the PPA hasn't been updated since 2013.

---

### Post by ardouronerous on 2018-07-17
The ppa:michael-gruz/canon-trunk doesn't work.

But good news, I managed to install my Canon printer 32-bit driver into 64-bit Lubuntu 16.04 and printed a Test Page after installing.
Here's how:

1. Download _cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz_ from [https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=87FC144EA2C54EF29F637118BB6D6231&ctype=dr](https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=87FC144EA2C54EF29F637118BB6D6231&ctype=dr)
Download _libtiff4_3.9.7-2ubuntu1_i386.deb_ from [http://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_i386.deb)
Download _canonip2700.ppd_ from [https://raw.githubusercontent.com/endlessm/cnijfilter-common/master/ppd/src/ppd/canonip2700.ppd](https://raw.githubusercontent.com/endlessm/cnijfilter-common/master/ppd/src/ppd/canonip2700.ppd)

2. Extract _cnijfilter-common_3.30-1_i386.deb_ and _cnijfilter-ip2700series_3.30-1_i386.deb_ from cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz

3. Enable 32-bit support in Lubuntu 64-bit by running these commands in the Terminal:
```
sudo dpkg --add-architecture i386
sudo apt-get update
```

4. Since CUPS isn't install by default in Lubuntu 16.04, install CUPS via Terminal:
```
sudo apt install cups
```

5. Go to System Tools -> GDebi Package Installer and run these deb packages in GDebi in the following order:
```
libtiff4_3.9.7-2ubuntu1_i386.deb
cnijfilter-common_3.30-1_i386.deb
cnijfilter-ip2700series_3.30-1_i386.deb
```
Reason for this is beacause when I tried to install the drivers via install.sh, it didn't work.

6. Go to System Tools -> Printers -> Add -> Select Device and select:
```
USB Printer #1 with status readback for Canon IJ
```
The device URL should be _cnijusb:/dev/usb/lp1_.
Then press Forward and Apply. _Do not Print Test Page when prompted._

7. Replace canonip2700.ppd found in _/usr/share/ppd/_ with the ppd you downloaded.
The reason for this is because the ppd from the original Canon driver is   limited in functions, the ppd from endlessm has more functions, like   printing in Fast Mode for example.

8. Go to System Tools -> Printers -> IP2700 -> Make and Model: Canon iP2700 series Ver.3.90 -> Change -> Choose driver -> Provide PPD file and select _canonip2700.ppd_ from _/usr/share/cups/model/_

9. Go to Printer Options -> Page Setup -> Page size and select:
```
Letter [8.50"x11.00" 215.9x279.4mm]
```
Reason for this is because when I first installed the driver, the page size was set to A4. If for you this is not the case, then skip this instruction.

10. In Printer Options, select your Print Quality. Personally, I prefer to print in Fast Mode, which is "4(Fast)", it's economical and it saves on ink. The driver available in the kernel, Canon iP2700 - CUPS+Gutenprint, doesn't have this option.

11. Go to Settings and Print Test Page.

---

### Post by wildmanne39 on 2018-07-17
Thanks for posting the solution, please use thread tools at the top of the page and mark the thread solved!:)

---

### Post by ardouronerous on 2018-07-17
Question, will enabling 32-bit support in 64-bit Lubuntu still be possible in the future? Because I heard 32-bit is being discontinued or is it just 32-bit ISOs?

---

### Post by kurt18947 on 2018-07-20
> **ardouronerous said:**
> Question, will enabling 32-bit support in 64-bit Lubuntu still be possible in the future? Because I heard 32-bit is being discontinued or is it just 32-bit ISOs?

Good job on persevering in your quest. I* think *discontinuing 32 bit support is just for 'mainline' Ubuntu. It'd be sorta silly to discontinue 32 bit support in a flavor intended for older/less powerful machines it seems to me. I did check and Brother, like Canon is supplying 32 bit drivers with 64 bit to 32 bit support so that's not uncommon.

---

### Post by ardouronerous on 2018-09-05
Updated instructions for Lubuntu 18.04 LTS:

[QUOTE=ardouronerous]
1. Download _cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz_ from [https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=87FC144EA2C54EF29F637118BB6D6231&ctype=dr](https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=87FC144EA2C54EF29F637118BB6D6231&ctype=dr)
Download _libtiff4_3.9.7-2ubuntu1_i386.deb_ from [http://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_i386.deb)
Download _canonip2700.ppd_ from [https://raw.githubusercontent.com/endlessm/cnijfilter-common/master/ppd/src/ppd/canonip2700.ppd](https://raw.githubusercontent.com/endlessm/cnijfilter-common/master/ppd/src/ppd/canonip2700.ppd)
[/QUOTE]

A new dependency is needed to make Canon PIXMA iP2700 32-bit driver work on 64-bit Lubuntu 18.04. 
Download _libpng12-0_1.2.54-1ubuntu1.1_i386.deb_ from [https://packages.ubuntu.com/xenial/i386/libpng12-0/download](https://packages.ubuntu.com/xenial/i386/libpng12-0/download)

[QUOTE=ardouronerous]
2. Extract _cnijfilter-common_3.30-1_i386.deb_ and _cnijfilter-ip2700series_3.30-1_i386.deb_ from cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz

3. Enable 32-bit support in Lubuntu 64-bit by running these commands in the Terminal:
```
sudo dpkg --add-architecture i386
sudo apt-get update
```

[s]4. Since CUPS isn't install by default in Lubuntu 16.04, install CUPS via Terminal:
```
sudo apt install cups
```[/s]
[/QUOTE]

In Lubuntu 18.04 LTS, no need to install CUPS since it's already installed by default.

[QUOTE=ardouronerous]
5. Go to System Tools -> GDebi Package Installer and run these deb packages in GDebi in the following order:
[/QUOTE]
```
libtiff4_3.9.7-2ubuntu1_i386.deb
libpng12-0_1.2.54-1ubuntu1.1_i386.deb
cnijfilter-common_3.30-1_i386.deb
cnijfilter-ip2700series_3.30-1_i386.deb
```

[QUOTE=ardouronerous]
6. Go to System Tools -> Printers -> Add -> Select Device and select:
```
USB Printer #1 with status readback for Canon IJ
```
The device URL should be _cnijusb:/dev/usb/lp1_.
Then press Forward and Apply. _Do not Print Test Page when prompted._

7. Replace canonip2700.ppd found in _/usr/share/ppd/_ with the ppd you downloaded.
The reason for this is because the ppd from the original Canon driver is   limited in functions, the ppd from endlessm has more functions, like   printing in Fast Mode for example.

8. Go to System Tools -> Printers -> IP2700 -> Make and Model: Canon iP2700 series Ver.3.90 -> Change -> Choose driver -> Provide PPD file and select _canonip2700.ppd_ from _/usr/share/cups/model/_

9. Go to Printer Options -> Page Setup -> Page size and select:
```
Letter [8.50"x11.00" 215.9x279.4mm]
```
Reason for this is because when I first installed the driver, the page size was set to A4. If for you this is not the case, then skip this instruction.

10. In Printer Options, select your Print Quality. Personally, I prefer to print in Fast Mode, which is "4(Fast)", it's economical and it saves on ink. The driver available in the kernel, Canon iP2700 - CUPS+Gutenprint, doesn't have this option.

11. Go to Settings and Print Test Page.[/QUOTE]

---


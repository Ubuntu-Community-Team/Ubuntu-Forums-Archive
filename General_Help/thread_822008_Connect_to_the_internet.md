---
title: "Connect to the internet"
date: 2008-06-07
forum: General Help
---

### Post by epic93 on 2008-06-07
I was wondering how I connect to the internet using my laptop running 8.04 ubuntu 64 bit. I have a conextant type 2 modem and I use dialup ([www.intergate.com](www.intergate.com)) I have been told I need drivers but simply cannot find them. Also, is it harder/impossible to find drivers for 64 bit ubuntu? i need detailed instructions on how to connect and if i need/location of drivers. If I need to switch to 32bit to get the drivers then I will so its ok if they are 32bit.

[CENTER]Thankyou in advance, epic93.


:guitar:


:lolflag::lolflag::lolflag:
:lolflag::lolflag::lolflag:
:lolflag:[/CENTER]

---

### Post by chronographer on 2008-06-07
look here: [http://ubuntuforums.org/showthread.php?t=190728](http://ubuntuforums.org/showthread.php?t=190728)

Maybe try this first:

the below mentions an application called kppp, so you caould install that first, see if it works out of the box! If not try below, its not as hard as it may seem! 


> Method B:

1.Put the downloaded file conexant_192-1ubuntu-1.tar.gz on your Desktop and right click &#8220;Extract Here&#8221; and a folder &#8220;conexant&#8221; will be created on your Desktop.
2.Read the txt files in the folder for more info.
3.Open the folder &#8220;conexant/modules/makefile&#8221;, right click on makefile, click Actions, then Edit as Root and Kwrite should open the file /conexant/makefile. Now find the 2 lines that start with # KERNELDIR? = /lib/modules..... etc. and KERNELDIR?= /usr/src... etc Remove the comment # in the first line and insert comment # on second line and save changes.
4.Now open the /conexant/makefile in the same way and find the commented line # rm -rf $$DESTDIR/dev/ttySHFS0. Remove the comments from the mentioned line and the following 3 lines up to &#8220;update modules&#8221; and save changes
5.cd Desktop/conexant
6.make
7.sudo make install
8.sudo modprobe hsfserial (you should get no result report if OK)
9.dmesg | grep hsfserial ( you should get no result report if OK)
10.The /dev/ttySHFS0 is created for the modem
11.To test, use the query modem on Kppp

To remove the installation:
rm /dev/ttySHFS0
rm -r /etc/hsf
rm /lib/modules/ARCH/misc/hsf*


Oops: looks like you may have to pay! [https://www.linuxant.com/store/faq.php](https://www.linuxant.com/store/faq.php)

---


---
title: "Canon Mf3010 doesn't work (no test page)"
date: 2014-09-13
forum: General Help
---

### Post by hicheme on 2014-09-13
Hi

I have installed canon mf3010, but it doesn't work, no test page !

what can I do ?

thanks

---

### Post by MrSteve on 2014-09-13
i found this thread on how to install your printer ...
[http://ubuntuforums.org/showthread.php?t=2089269](http://ubuntuforums.org/showthread.php?t=2089269)

---

### Post by pdc on 2014-09-13
so hicheme: 

are you using 64bit ubuntu?

You will need the Canon UFR driver; you download it from here; [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html?r=s&q=)

This is the 2.9 version and was updated 3rd July 2014;

I see they say they have evaluated this latest version as working on Ubuntu 13.10 both 32bit and 64bit ............ (as a linux grizzlie you are still allowed to harrumph that Canon don't support linux .................) 

It comes down as [COLOR="#008000"]Linux_UFRII_PrinterDriver_V290_uk_EN.tar.gz[/COLOR] and I can give you instructions on how to install; 

Can you open a terminal and paste this command in please ..................> [COLOR="#FF0000"]sudo /usr/sbin/lpinfo -v[/COLOR]      .............it asks about your printer connections ...............assuming they are usb .............and can you tell us the results please?

---

### Post by Binukattooran on 2014-12-05
network socket
network ipp14
network smb
network http
network lpd
direct hp
network ipp
network ipps
network https
direct hpfax

---

### Post by Binukattooran on 2014-12-05
got this result

---

### Post by pdc on 2014-12-05
this would sort of suggest your computer is not seeing your printer: go on, tell us a little more: ................it's a usb connection............. directly from computer to printer .............. on a stand-alone system ..........?

---


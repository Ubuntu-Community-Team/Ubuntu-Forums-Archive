---
title: "USB 2.0 MP3 player connects as USB 1.0"
date: 2005-10-09
forum: General Help
---

### Post by Quirky on 2005-10-09
I have recently bought a 'supratech' 1Gb MP3 player (it is similar to the last one shown on this page [http://www.supratech.es/FichaTecnica.asp?Ref=21](http://www.supratech.es/FichaTecnica.asp?Ref=21) ). It works fine - plug it in and it appears on the desktop as a 1Gb Removable Media, copy files across in nautilus, etc.

The only niggle is that in System->Administration->Device Manager it is shown under the USB 1.0 Controller. I have a 5 USB port laptop and have tried plugging the device in to each of the ports, but it doesn't seem to make a difference. It is shown as a USB 2.0 device, but under the 1.0 hierachy in Device Manager. As USB 2.0 is meant to be faster, I thought it would be better that it connected correctly. Anyone have any ideas what I can do or any other comments? Thanks in advance.

---

### Post by Mozzer on 2005-10-10
I am also suffering this problem with a Sumvision 512MB mp3 player. The file transfer does seem to be very slow... any help much appreciated.

Mozzer

---

### Post by Quirky on 2005-10-10
The only reference I have found that looks interesting is the following bug and forum thread:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=5153](https://bugzilla.ubuntu.com/show_bug.cgi?id=5153)
[http://www.ubuntuforums.org/showthread.php?t=9727](http://www.ubuntuforums.org/showthread.php?t=9727)

On my laptop (Fujitsu Siemens Amilo) there are no ehci error messages in dmesg, but the symptoms are certainly there. The bug report seems to say that it is fixed in Hoary, but it doesn't seem to be.

---

### Post by Mozzer on 2005-10-16
I entered the code on the Bugzilla page and got this:

```
root@ubuntu:/home/mozzer # dmesg|grep ehci
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xffa7fc00
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
ehci_hcd 0000:01:00.3: ALi Corporation USB 2.0 Controller
ehci_hcd 0000:01:00.3: irq 21, pci mem 0xff8ffc00
ehci_hcd 0000:01:00.3: new USB bus registered, assigned bus number 5
ehci_hcd 0000:01:00.3: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004

```

In other words, there doesn't seem to be any problems with USB 2.0 where other people got fatal errors, but it's definitely not the right speed.

---


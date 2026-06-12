---
title: "Win7 USB not detected"
date: 2014-07-31
forum: General Help
---

### Post by xdavis1990 on 2014-07-31
A couple months ago I got sick and tired of Windows 8. I absolutely despise Windows 8. So I decided to give Ubuntu a try, after a unreasonably difficult time installing Ubuntu(also Windows 8's fault) I succeeded and have fallen in love with the operating system. Only problem is that I'm a gamer. So I wanted to create a Windows 7 partition just to have steam on and be able to play windows games. I have tried various ways of creating a Windows 7 bootable USB. Including winusb, windows download tool from a virtual machine, and also using a friends windows machine to do so. No matter what I do my computer does not recognize that I have a bootable usb drive. It's not an option on my boot menu so I can't do a boot override from BIOS. Although it is a functioning usb drive as it works on other PCs and my usb port works fine, I have my keyboard plugged into it as we speak.

It's a fairly new ASUS laptop, 8GB ram, core i7 processor, nvidea 670mx card and I have only Ubuntu 14.04 installed right now. Any ideas what the problem is? And if more info is needed let me know.

---

### Post by mooreted on 2014-07-31
For Windows 7 I use the Windows 7 DVD Download Tool:

[http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool#usage](http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool#usage)

---

### Post by xdavis1990 on 2014-07-31
I did, the problem isn't the bootable usb. I have a working win7 bootable usb that will work on my other pc. But this computer doesn't even have it in it's boot menu. I can see it in ubunut, open it and browse around the drive. But I simply cannot boot it from this computer.

---

### Post by QIII on 2014-07-31
If the BIOS/EFI has no option to boot from USB media, I'm not sure we can be of help.  Do you have any documentation for your board?

---

### Post by quadrplax on 2014-07-31
What you want is something called [Plop boot manager]("http://www.plop.at/en/bootmanager/"). Burn it to a disk if your computer has a disk drive. This will allow you to boot to USB on any computer. I've used this thing on a Windows 98 machine and it even worked there. If you can't burn and boot to a disc then we're going to have to do something complicated like network booting. Do you have the exact laptop model? Also, this isn't necessary to run Windows software, you can use Wine from the store.

Edit: Didn''t see your system specs.

---

### Post by xdavis1990 on 2014-08-02
The PLOP boot manager worked! You are a lifesaver! And yeah I tried gaming through WINE with a little success, but trying to get the Witcher to not crash was impossible

---


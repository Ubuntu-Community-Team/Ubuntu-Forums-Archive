---
title: "Grub-install fatal error during installing Ubuntu 20.10 to USB drive"
date: 2020-11-23
forum: General Help
---

### Post by doughnut-dunker on 2020-11-23
Hi all,

During an Ubuntu 20.10 installation I received the error &#8220;Executing &#8216;grub-install/dev/sdb&#8217; failed. This is a fatal error&#8221;. I was forced to restart. Ubuntu loads when usb is plugged in and windows loads fine when usb isn&#8217;t plugged in.


However:

1) Can I check Ubuntu has been installed correctly/completely? GParted didn&#8217;t show up with the other apps nor in an app search, but in the software it said it was installed. I uninstalled/installed it and now it shows up but after clicking on the app icon it doesn&#8217;t start. Wasn't sure if this is related.(I tried &#8220;apt-get dist-upgrade and it returned all zeros).

2) Why is ubuntu running so slowly? It seems a lot slower than the USB trial ubuntu experience. Its almost freezing when just browsing through tabs in settings and the cursor keeps pausing and spinning when just navigating and loading apps in the OS. Again wasn't sure if this is related.

Thanks for any feedback. :p



BACKGROUND INFO: Installing Ubuntu 20.10 on a Sony-Vaio VPCSA3T9E [i7-2640 2.8Ghz x4, 7.7 GiB, 64-bit, Windows 7 Pro] but instead of on the local hard drive I wanted to try installing it on a 64GB USB SanDisk 3.1 (USB device B).


Changed the BIOS boot order (I think it&#8217;s Legacy BIOS) to external first and created a USB boot drive (USB device A) with Rufus. Before starting up the laptop I disconnected the internal hard drive. Once the Ubuntu test/install screen loaded I plugged in the 2nd USB device B into a different port to install ubuntu on.

During install I allocated 1,024mb to &#8220;/boot&#8221; (Primary; ext4), 2,000mb to &#8220;swap&#8221;, 20,000mb to &#8220;/&#8220; (Primary; ext4) and 30,000mb to &#8220;/home&#8221; (Primary; ext4).

---

### Post by doughnut-dunker on 2020-11-23
Actually,  I found a solution regarding Gparted not working. I was trying to load Gparted from the App Icon. It would ask for my password but after that didn't load. I then tried loading Gparted through terminal: $gparted - but was getting errors. However, when I tried terminal: $sudo gparted - it works just fine (Yay ^.^)

---


---
title: "Webcam with Microphone"
date: 2024-02-14
forum: General Help
---

### Post by Quarkrad on 2024-02-14
I've set up a vm (kvm) to run Zoom - and need to buy a webcam with microphone as I'm using my Desktop pc.  I'm worried about the device I buy not working - are there any issues/makes I should be aware of or can I assume any usb connected device will work?

---

### Post by Quarkrad on 2024-02-14
For example - if I bought this, and I've never come across this make, is there a risk it will not work?

[https://protechshop.co.uk/next-day-uk-delivery/aigoss-webcam-hd-1080p-for-pc-with-microphone-usb-computer-webcam-with-privacy/](https://protechshop.co.uk/next-day-uk-delivery/aigoss-webcam-hd-1080p-for-pc-with-microphone-usb-computer-webcam-with-privacy/)

---

### Post by TheFu on 2024-02-14
Only specific webcams are supported. Get one that is and is popular.  Support pages are littered with people who bough cheap webcams that don't work with Linux.

As much as I hate to recommend Logitech stuff, as they are fairly Linux hostile for non-support, I 100% know the C920 / C922 (1080) and C270 (720) webcams work with plug-n-use under a physical Linux.  I believe this is thanks to Google's ChromeOS, because before ChomeOS had lots of market share, the C920 did not work at all.

For a VM, I don't know and can see issues, especially with audio, which is common for VMs, IME.

---

### Post by dragonfly41 on 2024-02-14
Even an expensive Logitech webcam I purchased does not work on Ubuntu. Only when I boot into Windows does it work.

P.S.
Curious to see if my webcam matched those listed by theFu I followed this thread .. [https://askubuntu.com/questions/348838/how-to-check-available-webcams-from-the-command-line](https://askubuntu.com/questions/348838/how-to-check-available-webcams-from-the-command-line)

and so installed 

[FONT=monospace][COLOR=#000000]v4l2-ctl --list-devices[/COLOR]
Logitech BRIO (usb-0000:00:14.0-2.2):
        /dev/video0
        /dev/video1
        /dev/video2
        /dev/video3
        /dev/media0

[/FONT]

---

### Post by TheFu on 2024-02-14
BRIO is new and Logitech sucks at Linux support.  [https://askubuntu.com/questions/1250963/customizability-of-logitech-brio-4k-ultra-hd-webcam-on-ubuntu](https://askubuntu.com/questions/1250963/customizability-of-logitech-brio-4k-ultra-hd-webcam-on-ubuntu) does show people using it under Ubuntu.  I'd check the USB **Device ID** for kernel support.  [https://www.ideasonboard.org/uvc/](https://www.ideasonboard.org/uvc/) seems to be a supported USB video device list.   **lsusb** will show the device id.

---

### Post by him610 on 2024-02-14
We have two of these usb cameras, one is on a Xubuntu 22.04.3 machine, the other is on a Windows 11 machine. They both work without any issues. For a good price, listed for $19.99 today. Maybe you can purchase for equivalent price in UK.
[https://www.amazon.com/dp/B082X91MPP?psc=1&ref=ppx_yo2ov_dt_b_product_details]("https://www.amazon.com/dp/B082X91MPP?psc=1&ref=ppx_yo2ov_dt_b_product_details")

---

### Post by Quarkrad on 2024-02-15
After some research I bought a Logitech C270 and it works very well in my ubuntu-mate 22.04 host and vm.  TheFu was correct (as usual) in #3, the C270 just worked out of the box.

---

### Post by vanre on 2024-05-02
Test you webcam with mic in [https://webcammictest.io/](https://webcammictest.io/) where you can find online mic test headphone and webcam test for free.

---


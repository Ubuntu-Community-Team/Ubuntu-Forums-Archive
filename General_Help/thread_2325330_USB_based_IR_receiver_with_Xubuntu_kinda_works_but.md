---
title: "USB based IR receiver with Xubuntu kinda works but..."
date: 2016-05-21
forum: General Help
---

### Post by lircHelpPlease on 2016-05-21
as mentioned in title, USB based IR reciever brand Sony Model: PCVA-IR3U and remote control is RM-GP3 the strange thing is i do not have LIRC installed but it works kinda but, the input is all kinda strange, it does not do what it is supposed to do but some random stuff so i guess the buttons are wrongly mapped then again i wonder what makes it work if LIRC is not installed. thx for all the help in advance

---

### Post by TheFu on 2016-05-21
Kernels have added support for USB devices.  They pass keyboard events from any recognized HID USB device.

I have an RC6 remote connected via USB to a R-Pi v2 running Kodi. No LIRC needed, but I do have to make some /sys/ setting changes every reboot to prevent double clicks for any inputs.
"echo none +lirc > /sys/class/rc/rc0/protocols" is what I had to do.

---

### Post by lircHelpPlease on 2016-05-22
how do i map the buttons and functions and make that all work with KODI?

---

### Post by lircHelpPlease on 2016-05-24
anyone?

---

### Post by lircHelpPlease on 2016-05-25
bump

---

### Post by lircHelpPlease on 2016-05-25
i cant be the only one using IR remote functions well and TheFu obviously cause he/she replied

---

### Post by lircHelpPlease on 2016-05-26
bump

---

### Post by lircHelpPlease on 2016-05-27
bump

---

### Post by sailingboyLLB on 2016-05-27
i had an issue that i think is caused by bad XHCI drivers here:
[http://ubuntuforums.org/showthread.php?t=2304730&highlight=lirc](http://ubuntuforums.org/showthread.php?t=2304730&highlight=lirc)

---

### Post by lircHelpPlease on 2016-05-28
thx foir info,, are the XHCI drivers installed by default independent of hardware? or only with fairly new hardware, because my media computer is fairly old ca. 7 years old

---

### Post by lircHelpPlease on 2016-05-28
bump

---

### Post by lircHelpPlease on 2016-05-29
bump

---

### Post by lircHelpPlease on 2016-05-30
bump

---

### Post by sailingboyLLB on 2016-05-30
XHCI drivers are installed as needed.  it's the driver associated with USB 3.0 era USB.  if you computer doesn't have USB 3.0, it won't be an XHCI driver problem.

---


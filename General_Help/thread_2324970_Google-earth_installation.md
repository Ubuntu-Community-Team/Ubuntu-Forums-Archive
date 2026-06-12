---
title: "Google-earth installation"
date: 2016-05-17
forum: General Help
---

### Post by Mal_Ellis on 2016-05-17
I have recently installed Ubuntu 16.04 and all is well except getting Google-earth to run properly . When I start it up it flashes up on then screen and crashes out . I have installed, lsb-invalid, lsb-security, lsb-core, all 4.1 . Is there a compatibility problem with Ubuntu 16.04/Google-earth . I had Google-earth running very well in Ubuntu 14.04 with no problems from the first time I installed it . Could someone please take me through the whole installation process so that I can use Google-earth.
Running Ubuntu 16.04 Mate 1.12.1

---

### Post by Impavidus on 2016-05-18
This thread has some leads: [http://ubuntuforums.org/showthread.php?t=2321846&p=13481772](http://ubuntuforums.org/showthread.php?t=2321846&p=13481772)

I still dual-boot with 14.04, mostly to run GE there. It's even the 32 bit version on a 64 bit OS, but it's the only one I got working. More or less.

---

### Post by Linuxisfast on 2016-05-18
If you need lsb, best way is to add deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main to your repos on a freshly installed 16.04, then sudo apt-update and sudo apt install lsb after that remove the Trusty repo and install Google Earth, this works out best.

---

### Post by Mal_Ellis on 2016-05-18
thank you folks for the replies . Helped a lot and now got GE going ok .

---


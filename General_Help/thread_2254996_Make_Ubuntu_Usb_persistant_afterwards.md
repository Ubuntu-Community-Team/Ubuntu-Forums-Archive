---
title: "Make Ubuntu Usb persistant afterwards"
date: 2014-12-01
forum: General Help
---

### Post by tim78 on 2014-12-01
Is it possible to make the usb drive that ubuntu is running from perstent so I can save any software changes I make if I reboot?

---

### Post by nerdtron on 2014-12-01
What tool did you use to create it? In unetbootin (or any tool mostly) will let you set persistence when you create a bootable Ubuntu.

Now if you are currently running ubuntu without persistence, I would be better to just reinstall and create a persistence file in the first place.
Although it is possible to create one while already running ubuntu, it can get complicated. It's a lot easier to create it on the first place.

---

### Post by tim78 on 2014-12-01
Thank you. I used Universal Usb Installer but didn't notice the create persistent option and am now re-installing. Is everything automatic and I don't have to manually input and code or what not after being logged into ubuntu?

---

### Post by nerdtron on 2014-12-01
If the creation of persistence is correct, everything will be automatic.
Change the wallpaper and try to reboot. It the wallpaper persisted, then it's good.

---

### Post by tim78 on 2014-12-01
Thank you nerdtron :KS If you can maybe check out my recent post about missing menu fonts using wine. I really need to solve that as soon as I can.

---

### Post by tim78 on 2014-12-01
Okay, I re-installed it on a 7gb flash drive and selected 4gb persistence file size. I am noticing ubuntu is running much slower and downloads taking considerably longer than before when I didn't check create persistence drive. Is this normal, should I have selected a smaller persistence filesize?

---

### Post by nerdtron on 2014-12-01
Normal as the write speed on flash drives is considerably slower. Without persistence I think in only writes on RAM which is a lot faster.

---

### Post by sudodus on 2014-12-02
It is a good idea to get a fast USB 3 pendrive for persistent live systems. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---


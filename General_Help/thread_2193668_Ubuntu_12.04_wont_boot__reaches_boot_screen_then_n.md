---
title: "Ubuntu 12.04 wont boot / reaches boot screen then nothing"
date: 2013-12-14
forum: General Help
---

### Post by REMIX8604 on 2013-12-14
Hello all,

I am having trouble with my laptop today. I think one of 2 things broke my OS.(1) I updated the graphics drivers and (2) I tryed to make a steamOS USB. I restarted the computer with the USB stick in the laptop. It gave me an error saying it cant boot. So I took out the USB, turned the laptop back on. Now I get the purple boot screen for a sec and then it goes black with that little blinking dash mark on the top left. nothing after that.

Im sure it was my actions that broke something. What steps should I take to troubleshoot and fix this?

Notes: 
I made a live USB and I'm working off it now.
Ctrl + Alt + F2 don't work at the boot screen.
I noticed after the screen goes black it connects to another laptop (I've been using for hotspot). This makes me think it's the graphics driver.

---

### Post by grahammechanical on 2013-12-14
So, you get a Grub Menu? Try selecting Recovery Mode. In 13.04 or 13.10 we find it under the Advance Options for Ubuntu submenu. At the Recvoery menu select resume. That will sometimes get us to a desktop using an unaccelerated video drvier as a fallback. From there you can change video drivers.

In trying to make that SteamOS USB did you let it put its Grub on to the USB or did you let it put its Grub on sda? If it is the second option then Grub on the hard disk is looking for an OS to boot on the USB stick.

In a live session use file manager to open the hard disk and then in a terminal run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

I am assuming that you only have one hard disk (sda). In a live session you may not need to put sudo at the front of those commands. Oh, by the way, the Recovery menu gives us an option to update Grub. So, we can also do it from there.

Regards.

---

### Post by REMIX8604 on 2013-12-15
> **grahammechanical said:**
> So, you get a Grub Menu? Try selecting Recovery Mode. In 13.04 or 13.10 we find it under the Advance Options for Ubuntu submenu. At the Recvoery menu select resume. That will sometimes get us to a desktop using an unaccelerated video drvier as a fallback. From there you can change video drivers.

Thank you! I got it to work. I followed what you said here but got an error after "checking battery state". My battery is shot so maybe that's why it gave an error and got hung up on me. I solved this by going to the GRUB menu, then selecting choose a previous Linux version. After choosing an older version I could get the "resume" option you mentioned and did not get an error. It did fallback to another video driver. Then I just changed drivers from there and a quick restart! :D

---


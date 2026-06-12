---
title: "OK I am on Ubuntu 14 on a USB  as I type.  Thanks for the help.  Next?"
date: 2015-09-07
forum: General Help
---

### Post by Boyntonstu on 2015-09-07
sudu is asking for a password.  What is that all about?

I want to install my headphone for the mic and earphones.

How?

---

### Post by QIII on 2015-09-07
Hello!

Type your password carefully and press enter.  You won't see anything on the screen, not even asterisks.

If you are the original user created during setup, that password is the same as the one you use to log in.

---

### Post by Boyntonstu on 2015-09-07
Mystery!!!  Wow!
What app for headset and mic control?

---

### Post by Dennis N on 2015-09-07
Try Pulse Audio Volume Control. Ubuntu: It's likely already installed.

Edit: It's installed by default in Xubuntu 14.04, but not in Ubuntu (according to the package manifest).

---

### Post by Bucky Ball on 2015-09-08
*Thread moved to **General Help**.*

For future reference: it really helps if your thread title describes your issue and you provide as much info as you can. This one doesn't give a hint. You might like to check the third link in my signature. Also, one question a thread will get things rolling faster. More than that can cause confusion. In this case, the first question was easy to answer so all good. :)

Plug in the mic and headset, open Pulseaudio Volume Control, get an audio stream happening (play a song), check the output tab and set the headphones as the output device. Check the input tab and set your mic as the device.

If you don't have Pulseaudio VControl installed, install from Software Centre or Synaptics.

---

### Post by Boyntonstu on 2015-09-08
I understand, thanks.

Got pulseaudio and V control.

BYW running Lubuntu 100% on a 32  GB USB 3.0 stick is plenty fast enough for me.

Although I do not have a USB 3.0 port, I figured that for the same price as a 2.0 device,  the chip  would have a higher speed capability.

At this time Lubuntu on a stick screams in comparison with Win 7.

---

### Post by Bucky Ball on 2015-09-08
... but if the Ubuntu on a stick is not a persistence install you will lose all settings when you reboot. Guess you're aware of that. If you install drivers they won't be there on a reboot.

Do you actually want support with anything here? Best to start a new thread for audio issue, descriptive title and give all details. See third link in my signature. Good luck.

---

### Post by Boyntonstu on 2015-09-08
[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by efflandt on 2015-09-09
Bucky Ball, the OP did not say (in this thread) if it was a live/install iso or regular install [especially since he(?) mentions that it screams]. For example I have full install of both 64-bit Lubuntu and Ubuntu 12.04 (sharing common /home partition) on 32 GB SD card that my tablet PC can boot from (its only internal storage is Win7 Pro on 32 GB SSD). That may not scream with its 1 GHz 2 core CPU and 2 GB RAM, but runs quicker than Windows. If it is a full install anything can be done that can be done on any other installed system, as long as there is space left. That is different than live/install system on iso (which probably would not scream), where with persistence programs can be added that still work after booting, but things that happen during boot like kernel updates or added video drivers will not work on the iso since it boots from a fixed squashfs file system.

---

### Post by yancek on 2015-09-09
> Although I do not have a USB 3.0 port, I figured that for the same price  as a 2.0 device,  the chip  would have a higher speed capability.

The device is limited by the port, if you have a 2.0 port it doesn't matter if you have a 3.0 usb.  For the same price though, might as well.  Good buy.

> Bucky Ball, the OP did not say (in this thread) if it was a live/install  iso or regular install [especially since he(?) mentions that it screams

True.  He did post a link in his last post to a site explaining a persistent install so I would imagine that's what he has done.

---

### Post by sudodus on 2015-09-09
> **yancek said:**
> The device is limited by the port, if you have a 2.0 port it doesn't matter if you have a 3.0 usb ...


This is true sometimes, but a pendrive's speed is often limited by the flash hardware. In such cases you can find USB 3 pendrives with faster flash hardware, that can match the full capacity of the USB 2 interface, and then it does matter if you have a 3.0 usb pendrive.

See [this link](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085).

---


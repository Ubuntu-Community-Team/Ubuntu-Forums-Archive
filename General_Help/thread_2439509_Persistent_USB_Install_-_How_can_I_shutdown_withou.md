---
title: "Persistent USB Install - How can I shutdown without removing USB?"
date: 2020-03-28
forum: General Help
---

### Post by carl-leach-public-b on 2020-03-28
I have created a persistent USB Ubuntu install, which works exactly how I want, except for shutdown where is asks for the USB to be removed and press enter. I'm running the install on a touch panel thin client which doesn't have a keyboard, so pressing enter is not possible and I don't want to remove the USB, I want the system to just shutdown whilst the USB is still plugged in and without any further interaction, Is this possible?

---

### Post by ajgreeny on 2020-03-28
Wait for more answers before accepting mine, but having got to the "Remove install medium and press ENTER" you can simply press the power button to switch off.

By that point the USB is unmounted so will not suffer in any way.
Unfortunately I do not know of a way to get that to happen as the default action.

---

### Post by crip720 on 2020-03-28
As long as you realize that the computer will probably boot back to the USB installer on next start up, you should be good to leave it in.  Just remember a persistent USB installer does not have the same dependability as an installed system.

---

### Post by dragonfly41 on 2020-03-28
xdotool?

---

### Post by C.S.Cameron on 2020-03-29
If you want a Live or Persistent install use mkusb to make the drive that does not require removing USB. 
[https://askubuntu.com/questions/855696/can-a-persistent-ubuntu-install-be-made-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855696/can-a-persistent-ubuntu-install-be-made-to-the-pendrive-it-was-booted-from)

If you do not need the USB for installing Ubuntu, you can do a Full install to it and it will be just like an internal install. 
[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-19-10-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-19-10-to-usb-device-step-by-step)

---

### Post by HermanAB on 2020-03-29
Hmm, in my experience it is is better to just do a regular install to a USB storage device, rather than using the overlay file system persistent USB Rube Goldberg Machine.

---


---
title: "Guitar Hero Xplorer no longer works"
date: 2008-06-01
forum: General Help
---

### Post by Boktai1000 on 2008-06-01
Hello, after installing the xpad driver for the xbox 360 controller by following the guide here [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) when I plug my X-plorer Guitar in (its the USB 360 version that comes with Guitar Hero II) it dosnt function, it lights up upon putting it into the usb but blanks out right after.  Ive tried removing my 360 wireless receiver and just having the Guitar in and it didnt seem to work either, ive also tried unplugging the 360 wireless receiver and plugging in the Guitar and rebooting which only results in Ubuntu not loading at start up.  If anyone can help I would be very grateful as i really want to play some frets on fire :guitar:

thank you for your time
Boktai1000

---

### Post by Boktai1000 on 2008-06-02
Even if anyone knows how to just get 1 working at a time that would be helpefull but id like to have them both working if possible.

edit: I just actually plugged my Guitar Hero Xplorer in after boot and did these commands.

sudo depmod -a
sudo modprobe xpad

and i went into Frets on Fire and tried to keybind something and it worked :guitar: im not gona complain now that its working but i hope one day this bug is fixed so others wont have to go through this same situation.

edit2: btw unplugging and replugging the guitar back in while in the same session will make the guitar not work, but a simple reboot it seems fixs that.

---


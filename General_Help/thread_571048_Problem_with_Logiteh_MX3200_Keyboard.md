---
title: "Problem with Logiteh MX3200 Keyboard"
date: 2007-10-08
forum: General Help
---

### Post by calder0n on 2007-10-08
Hey,
I just bought a Logitech MX3200 Keyboard (+ MX600 Laser Mouse) combo, and I'm having trouble getting the wireless keyboard to work in Ubuntu 7.04 . It looks like other people have trouble with the mouse but in my case it worked perfectly.

```
Oct  8 18:17:03 sophie kernel: [   18.022853] input: Logitech USB Receiver as /class/input/input3
Oct  8 18:17:03 sophie kernel: [   18.022921] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-1
Oct  8 18:17:03 sophie kernel: [   18.051328] input: Logitech USB Receiver as /class/input/input4
Oct  8 18:17:03 sophie kernel: [   18.051527] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-1
Oct  8 18:17:03 sophie kernel: [   18.051547] usbcore: registered new interface driver usbhid

```

ANd it looks like its detecting it properly, but no luck.

Is there anything I should also add to my Xorg.conf?
Any other ideas?

THanks.

---

### Post by demisgc on 2007-10-10
Hello buddy, i had the same problem with this keyboard on linux. The fact is that the mouse do not use encryption in order to conect to receiver but the keybord does. To do it work you must configure it on a windows machine first. Install the logitech software that comes with the keyboard. On the logitech desktop software configure you keyboard to use encryption (the software will guide you throuhg the process) and it's done. Now just plug the receiver on linux and everything will work fine. Just a remark the extra functions do not work on linux (voip key, www key and so on) just the regular keyboard works. If you have any doubt fell free to contact me.

Kind regards,

Demis

---

### Post by arrrghhh on 2007-12-01
that seems like a big pain, and i'm guessing they fixed this in 7.10, because i didn't have any problem whatsoever.  just connected it, and it works.

what my question is, is there any way to use the extra features at all?  like can i program the presets, set the www key to firefox, etc?

what is interesting to note, none of the "extra" buttons work - except for the calculator button.  for me, it fires SpeedCrunch up right away!

---


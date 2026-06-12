---
title: "Installer puts bootloader on USB key"
date: 2014-07-23
forum: General Help
---

### Post by Cryonicblue on 2014-07-23
Hi. I'm having problems installing ubuntu (mini.iso) for the first time ever

I install from a usb stick to a harddrive. This has worked fine for me in the past but now I'm stuck with a black screen with blinking cursor when trying to start.

I assume some kind of bootloader (sorry if I'm using the incorrect term here) is put on the USB instead of the harddrive because if I put the USB key in it boots up.

How do I avoid this?

---

### Post by sudodus on 2014-07-23
Which version of mini.iso are you using? Version 14.04 LTS should work from USB, while version 12.04 LTS only works from CD/DVD.

Select ***Something else*** for the partitioning screen.

You can check which drive is which during installation by getting into a second text screen with the hotkey combination ***ctrl + alt + F2***.

There you can run the commands

```
sudo parted -l
```
and
```
df
```

to identify which device is the USB drive and which is the internal drive. df shows the root partition '**/**' for the drive you are booting from.

Then you can return to the installer with the hotkey combination ***ctrl + alt + F1*** and select the correct drive for the bootloader.

---

### Post by Cryonicblue on 2014-07-24
I resolved this issue. I simply removed the USB stick when the installer chose a network source to install from so it only had the harddrive to put stuff on later on and could not split things up.

---

### Post by sudodus on 2014-07-24
Congratulations! You found a solution yourself :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---


---
title: "Can't boot rasbery pi from USB"
date: 2021-10-27
forum: General Help
---

### Post by thenchanted on 2021-10-27
[COLOR=#333333][FONT=&amp]Can't boot from USB SSD, on SSD Ubuntu (Ubuntu Server 20.04.3 LTS 64-bit) for Raspberry Pi4 8gb

[/FONT][/COLOR]

---

### Post by deadflowr on 2021-10-28
*Thread moved to **General Help***

---

### Post by sudodus on 2021-10-28
1. Older Raspberry Pi computers booted only from the SD card slot. Are you sure that your version of RPi can boot from USB?

2. Is your Ubuntu Server made for *your* RPi (is it the correct version of image file)?

3. How did you create the USB boot drive (which tool/method did you use)?

---

### Post by thenchanted on 2021-10-28
1. It should boot out of the box, especially 8gb model

2. yea, Raspberry Pi imager v1.6.2

3. None...
P.S Adapter from ssd m.2 to RP Is based on [COLOR=#555555][FONT=Roboto]ASMedia chip[/FONT][/COLOR]

---

### Post by axelmasok on 2021-10-29
I'm reading it's a convoluted process.

- Does the m.2 with adapter work at all as a boot device on something typical like a laptop/desktop?

- The process to prep a USB drive looks like it involves prepping an SD card, boot off the SD card, prep the USB drive from there, then boot off USB.

---

### Post by sudodus on 2021-10-29
1. Please describe with more details how the operating system was installed or cloned or copied into the m.2 stick.

2. I agree with @axelmasok that you should make sure that the adapter with the ASMedia chip works for booting. Please check that.

---

### Post by thenchanted on 2021-10-29
1. Connected it by USB PAPA TO PAPA TO My main [COLOR=#000000]computer and used [/COLOR][COLOR=#000000]Raspberry Pi imager

2. Adapter/case is Argon ONE m.2

3. I don't know how to check it

Edit: google'd and found
[/COLOR]

---

### Post by sudodus on 2021-10-29
Sounds good that you used Raspberry Pi imager.

You could check the adapter if you overwrite the RPi image with an Ubuntu amd64 iso file for a computer and try to boot your computer from it. Try Ubuntu live, do not install. (If it works, it is likely to work also to boot your RPi.)

If that worked you can clone the RPi image with the Raspberry Pi imager again and more with it. Otherwise you could try with a USB pendrive, that is big enough for the image.

---


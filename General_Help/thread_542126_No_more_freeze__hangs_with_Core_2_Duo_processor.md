---
title: "No more freeze / hangs with Core 2 Duo processor"
date: 2007-09-03
forum: General Help
---

### Post by Satman on 2007-09-03
I Just wanted to share my :) now my ubuntu feisty kde 64 bit runs super stable on a Intel core 2 duo E6600.
Being a linux/ubuntu user only for a year I had mixed feelings about linux/ubuntu because it on one hand starts up and works fast with OpenOffice and internet surfing etc, but on the other hand it sometimes hanged/freezed in more demanding tasks like transcoding videostreams with ffmpeg or vlc , or installing large packages with dpkg. I could workaround these problems in recovery mode, but this made me a not so happy ubuntu-camper.

The trick  was adding acpi=ht to the kernel startup line in the boot-loader, in my case Grub.
With > sudo gedit /boot/grub/menu.lst I've now permanently added acpi=ht at the end of the kernel boot line so it starts up every time.

Now I cam startup 2 transcoding sessions simultaneously , putting both processors at nearly 100 % load, and still work with other things without worrying about a sudden death.
:guitar:
Although acpi is meant to manage power usage (especially effective in laptops), it has a tremendous effect on the stability on my 'ordinary' self-assembled miditower-box.

Hopefully this info is to some help to someone.
Please do report if it helped (or not).

---


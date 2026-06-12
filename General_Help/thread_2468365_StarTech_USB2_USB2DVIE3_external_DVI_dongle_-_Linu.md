---
title: "StarTech USB2 USB2DVIE3 external DVI dongle - Linux driver?"
date: 2021-10-26
forum: General Help
---

### Post by nginmu on 2021-10-26
EDIT.. marked thread as solved due changing focus to a different device based on a newer DisplayLink chipset, which I'm fairly sure does enjoy good Ubuntu support.

Can anyone give any pointers as to whether an Ubuntu driver might be available for a StarTech USB2DVIE3, which is a USB 2.0 to DVI external graphics card?

It uses a chipset from a Taiwanese company, Magic Control Technology (MCT). Chipset is Trigger T2-285B.

I've previously tried installing a "Lindy" brand, DisplayLink DL-165 based USB 2.0/VGA device to run a 3rd monitor on my laptop & although it worked using the DisplayLink Linux driver, it was unusably jerky & slow so I'm trying out alternatives.

I guess I'm never going to get perfection because I only have USB 2.0 available on my HP G72 laptop, but just something that works acceptably well for word processing, email etc would be great.

---

### Post by dragonfly41 on 2021-10-26
I see that you solved this but just in case ...

[https://www.startech.com/en-gb/audio-video-products/usb2dvie3](https://www.startech.com/en-gb/audio-video-products/usb2dvie3)

---

### Post by nginmu on 2021-10-26
Thanks for the link. Quite by chance following on from there I stumbled across a different one of theirs, this one explicitly provides an Ubuntu driver direct from the manufacturers site.

[https://www.startech.com/en-gb/audio-video-products/usb2dvipro](https://www.startech.com/en-gb/audio-video-products/usb2dvipro)

512Mb & does mention it's backward compatible with USB2. DisplayLink DL-3100 chipset.

The old Lindy 42744 / DL-165 VGA converter I was trying had, beside the DisplayLink chip, a N2DS12816FS-5T memory chip which as far as I can tell is only 8Mb.. so I'm hoping 64 times the memory plus the newer chip might result in less sluggish performance.

---


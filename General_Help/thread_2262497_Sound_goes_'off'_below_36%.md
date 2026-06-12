---
title: "Sound goes 'off' below 36%"
date: 2015-01-25
forum: General Help
---

### Post by Andrew_Lucas on 2015-01-25
Hi all,

Firstly, apologies if this should be posted into one of the subforums.

I've recently come back to Xubuntu after a period of enforced Windows usage. I don't remember this being a problem before, but it has been about a year since I used Xubuntu/Linux last. Still, I'm reasonably sure this is a 14.10 issue.

The title more or less says it all. Sounds goes from clearly audible, and if not loud, not quiet (36%/-26.89dB volume according to 'Pulse Audio Volume Control') to off at 35%/-27.3dB. This is consistent across internal speakers and a USB headset. It also seems to occur in programs (e.g. I can cause the same effect by sliding the volume in both the panel and by doing so in Audacious - and VLC too). I emphasise, it's not just really quiet, it's completely inaudible at 35%.

The other odd thing I noticed is once after rebooting, ALSA had muted itself without being told to. I only really use the GUI for controlling the volume, and had to install the alsa-utils package and unmute the soundcard through the terminal. It's only happened once but it's odd and I wondered if it was related?

Obliviously this isn't a deal breaker but it would be nice to be able to lower the volume e.g. at night or other quiet times.

Soundcard (LifeChat is the headset):

LinuxLaptopPC:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7e10000 irq 46
 1 [LX3000         ]: USB-Audio - Microsoft LifeChat LX-3000
                      Microsoft LifeChat LX-3000 at usb-0000:00:14.0-2, full speed

The laptop is an Asus X551CA.

Any help welcome, cheers!

EDIT: I've really no idea how to track down where the problem would be with this, so if anyone needs more info, give me the commands and I'll post the output.

---

### Post by Andrew_Lucas on 2015-01-26
BUMP.

Also, I've I can make the volume quieter by turning the volume in the panel down to the minimum it's capable of (36%) and then turning the program volume down (e.g. using the slider inside Audacious/VLC). It's an irritating work around, but it does *seem* to work.

A more permanent fix, or at least an explanation of what's wrong, would still be welcome.

---


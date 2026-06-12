---
title: "Computer freezing during booting, maybe gdm related?"
date: 2007-02-18
forum: General Help
---

### Post by paulyg on 2007-02-18
Yesterday we had the power go out. I was reading a web page at the time. Since then my computer will not boot up into Ubuntu. I get the splash screen with the ubuntu logo and red progress bar. Then I get a "wait" mouse icon, the little stopwatch or clock looking thing. Then I get a grey box about 1" x 1" in the center of the screen that quickly disappears. Then the monitor "turns of" or goes into power saving mode, then comes back on, then goes off again. At this point the system will not respond to keyboard or mouse inputs.

I did a lot of searching yesterday. I am able to boot into "recovery mode". I get a terminal prompt. I was able to get gnome to launch using "startx", though I had no mouse control, presumably b/c it is a usb mouse. Since it gets all the way to where it looks like it is starting up X or gdm I figured the problem lies with one of those two. I found a lot of posts yesterday instructing people to "dpkg-reconfigure xserver-xorg" and "dpkg-reconfigure gdm" if gnome was crashing or not starting. I ran both. I got two screens through the xserver-xorg confgure program and something locked up as I was trying to give a name to my graphics device. So I booted back into recovery mode and looked at my xorg.conf. Everything looks OK. I am using the i810 driver if that makes any difference. When I reconfigured gdm it did give me some message or warning, but I don't remember what it was.

I also brought up dmesg and everything looked ok there too. At the beginning of the file there were a bunch of things starting with "APCI:" but they did not look like error messages to me. But I don't know what an actual error message looks like.

At this point I am at the end of my knowledge and don't know what else to do. Did the power failure cause part of the disk to get corrupted and the corrupt area happens to be in the gdm area? How would I check for that? During the recovery mode boot fschk rand and said everything is OK but that is not a complete scan is it? Could it be an ACPI issue?

Any help is appreciated.

---

### Post by paulyg on 2007-02-18
I forgot to mention. This is a 6.10 Edgy system.

---

### Post by paulyg on 2007-02-18
Bump. Help anyone?

---


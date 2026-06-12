---
title: "Sound from programs inside a chroot"
date: 2017-05-01
forum: General Help
---

### Post by charononus on 2017-05-01
[COLOR=#1D2129][FONT=Helvetica]Ok so I finally got a project of mine mostly working. I'm running Ubuntu 16 amd64 and have Retropie installed. Because it uses a custom sdl2 I had to install PCSX2 inside a chroot. I've gotten that mostly working. It runs, it accepts gamepad input, etc. The one problem that I'm having is that no program from inside the chroot can actually produce sound on the computer.[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]I've mounted a few folders into the chroot already with[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]sudo mount -o bind /proc /srv/chroot/xenial[FONT=inherit]/proc/
sudo mount -o bind /dev /srv/chroot/xenial/dev/ 
sudo mount -o bind /home /srv/chroot/xenial/home/
sudo mount -o bind /sys /srv/chroot/xenial/sys/[/FONT][/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit]I have a feeling I'm missing something stupid, any ideas?[/FONT]
[/FONT][/COLOR]

---

### Post by &amp;KyT$0P# on 2017-05-01
Does also mount-binding [FONT=Courier New]/run[/FONT] make any difference?

---

### Post by charononus on 2017-05-04
> **halogen2 said:**
> Does also mount-binding [FONT=Courier New]/run[/FONT] make any difference?
Sorry for not getting back sooner,  life got hectic for a bit.  I just tried this and it had no effect.

---


---
title: "grub2 has black borders on the sides and top &amp; bottom"
date: 2015-01-06
forum: General Help
---

### Post by alfred8 on 2015-01-06
[COLOR=#222222]Hi All,[/COLOR]

[COLOR=#222222]I am having issues with grub2 showing in full screen mode. I have an LG 27" monitor with 1920x1080 resolution and when grub2 menu shows it has black borders on the sides and top and bottom.[/COLOR]

[COLOR=#222222]Is there anyway I can get it to show without the black borders?[/COLOR]

[COLOR=#222222]Regards,[/COLOR]

[COLOR=#222222]Alfred G.[/COLOR]

---

### Post by ibjsb4 on 2015-01-07
My 22" monitor is 1920x1080.  Are you using the wrong res?

Saying you run grub2 doesn't say much.  What ubuntu and what version do you run?

---

### Post by alfred8 on 2015-01-09
Hi ibjsb4,

I'm using Ubuntu 14.04 LTS.

Regards

---

### Post by grahammechanical on 2015-01-09
I have a digital TV as a monitor and it shows a black border all around the motherboard splash screen and the Grub background image. I understand this to be because the motherboard is running a video mode that is expected to be compatible with a wide range of monitors and display screens as well as graphic adapters.

We do not get a video driver loaded until after the display server (Xserver) is loaded and that only loads after we have launched the loading of Linux from the Grub menu. I am not troubled by this fact of life because the situation exists for only a few seconds.

There is a Grub manual that explains about the video modes that Grub 2 can be set to. Personally, I would not risk messing up the Grub configuration by editing Grub configuration files. Not for something that only lasts a few seconds.

[https://www.gnu.org/software/grub/manual/](https://www.gnu.org/software/grub/manual/)

[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

Regards.

---


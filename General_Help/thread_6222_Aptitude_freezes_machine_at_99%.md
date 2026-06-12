---
title: "Aptitude freezes machine at 99%"
date: 2004-11-26
forum: General Help
---

### Post by arpa on 2004-11-26
I tried to update & install some packages with aptitude, but after 99% it freezes the computer. HD & CD activity lights are lit, but keyboard doesn't seem to react in any way. So I had to use the power button. 

Has happened twice (out of two tries...)

I installed Ubuntu without X or Gnome (custom-expert) and it went well.

Also if I select finnish part of the installation program is in swedish (very bad :) and at least Vim is in swedish after installation. It should use english version instead if finnish isn't available.

AMD K6/200/256MB/15GB

and one additional question, how can I change the terminal size (not using X server) like in dos mode 120,50 for example. I'm sick of 80x40 screen :)

---

### Post by ubuntu_demon on 2004-11-26
Why don't you use apt-get or synaptic for your package-management ?

---

### Post by p!=f on 2004-11-26
Does the update/upgrade process work with apt-get update/upgrade?

For the framebuffer resolution...
Under root privileges open /boot/grub/menu.lst (I suppose you use GRUB as a bootloader) and find a line which starts with...
(for every kernel)
```

# kopt=root=/dev/hda3 ro **vga=791** video=vesafb:ypwrap,mtrr,pmipal

```
```

Here is an explanation of the values you can use:

vga=xxx sets the framebuffer console to a specific resolution.
Here is a table you can use so it can help you decide
what resolution you want to use:
      colour          depth   | 640x480  800x600  1024x768 1280x1024
      256             (8bit)  |  769      771       773      775
      32000           (15bit) |  784      787       790      793
      65000           (16bit) |  785      788       791      794
      16.7 Mill.      (24bit) |  786      789       792      795

```
Choose your resolution and run
```

sudo update-grub

```

---

### Post by arpa on 2004-11-26
[QUOTE=demon666_nl]Why don't you use apt-get or synaptic for your package-management ?[/QUOTE]

Well I might, but aptitude should not crash the computer anyway should it? And as being new to Debian packet management in general, I wanted to see what packages are available, get a list view sort of. Can you have that with apt-get?

---

### Post by ubuntu_demon on 2004-11-26
synaptic rules for having overviews

---


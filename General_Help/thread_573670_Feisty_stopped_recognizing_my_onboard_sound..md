---
title: "Feisty stopped recognizing my onboard sound."
date: 2007-10-11
forum: General Help
---

### Post by Sparky222B on 2007-10-11
I haven't really had any problems with ALSA lately, but I just ran a system update today, and I haven't had any sound since.

I checked the GNOME audio panel, and later alsamixer, only to find that my onboard sound isn't even there..?

```

alsamixer: function snd_ctl_open failed for default: No such device

```

[img]http://img171.imageshack.us/img171/3304/wtfok5.png[/img]

What the heckkk?

---

### Post by Sparky222B on 2007-10-13
Bump...help me?

---

### Post by Sparky222B on 2007-10-14
Still need help.

---

### Post by mali2297 on 2007-10-14
Did your sound work out of the box when you installed Feisty or did you have to compile the driver yourself? In the latter case you probably had a kernel update and now need to recompile driver.

...**or** perhaps a better option: Upgrade to Gutsy when it is released in a few days.

---

### Post by mali2297 on 2007-10-14
If you didn't compile the driver yourself, it might just help to reinstall the alsa utilities:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop

```
(Copy/paste into the terminal.)

Then check
```

aplay -l
lspci -v | grep -A 5 [Aa]udio

```
What's the output?

---


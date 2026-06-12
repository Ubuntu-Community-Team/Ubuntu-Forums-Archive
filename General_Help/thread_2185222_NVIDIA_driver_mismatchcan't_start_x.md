---
title: "NVIDIA driver mismatch/can't start x"
date: 2013-11-01
forum: General Help
---

### Post by bezolaam on 2013-11-01
[COLOR=#789922][FONT=arial]>use ubuntu 12.04[/FONT][/COLOR]
[COLOR=#789922][FONT=arial]>switch to nvidia driver which is "recommended" in drivers' section[/FONT][/COLOR]
[COLOR=#789922][FONT=arial]>can't start x after restart[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]wat do?[/FONT][/COLOR][IMG]http://i.imgur.com/iOs4AaM.jpg[/IMG]

---

### Post by grahammechanical on 2013-11-01
How did you install/activate Nvidia 319.32? Through additional drivers? That utilty usually prevents a mismatch such as this.

At the Grub menu you can selection Recovery Mode and at the Recovery menu you can select Resume and that should get you to a desktop without loading a video driver. At the desktop you can use Additional Driver to experiment with other video drivers. Perhaps you need to reinstall/activate Nvidia 319.32

Regards.

---

### Post by bezolaam on 2013-11-01
[COLOR=#000000]>How did you install/activate Nvidia 319.32? Through additional drivers? That utilty usually prevents a mismatch such as this.

yep, exactly, from [/COLOR][COLOR=#000000]additional drivers. Will try as you said, will report soon[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by bezolaam on 2013-11-01
> **grahammechanical said:**
> How did you install/activate Nvidia 319.32? Through additional drivers? That utilty usually prevents a mismatch such as this.

At the Grub menu you can selection Recovery Mode and at the Recovery menu you can select Resume and that should get you to a desktop without loading a video driver. At the desktop you can use Additional Driver to experiment with other video drivers. Perhaps you need to reinstall/activate Nvidia 319.32

Regards.

this doesn't help, but i fixed with this:
> jockey-text --list
jockey-text -d xorg:nvidia_319
jockey-text -e xorg:nvidia_304

---


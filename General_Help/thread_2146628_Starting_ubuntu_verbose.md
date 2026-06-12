---
title: "Starting ubuntu verbose"
date: 2013-05-19
forum: General Help
---

### Post by dagring on 2013-05-19
I have disabled the Plymouth theme, and watches the system messages run over the screen at startup. Nice and interesting, but the problem is the screen resolution is about 800x600. It ishould be 1280x1024. I have tried to change this in /etc/default/grub, but it doesn't change. 

Have anybody a clue about how to fix this?

Dag R

---

### Post by sudodus on 2013-05-19
See this link [https://help.ubuntu.com/community/Grub2/Displays#Resolution_Settings](https://help.ubuntu.com/community/Grub2/Displays#Resolution_Settings)

> The images in the *grub2-splashimages* package are primarily 640x480 images. 

GRUB 2 looks for a resolution setting in */etc/default/grub*. ***If uncommented***, the resolution is determined by this line: 

[LIST]
[*][TABLE]
[TR]
[TD="bgcolor: #fffbdb"]GRUB_GFXMODE=640x480[/TD]
[/TR]
[/TABLE] 
[*]If no setting is found in */etc/default/grub*,  GRUB 2 attempts to use the highest resolution possible. GRUB 2 may not  be able to handle the same resolutions as the computer can once the  operating system is booted. 
[/LIST]


Run ```
sudo update-grub
``` to make the change active

It might be a little tricky to find a resolution that really works. At the grub menu (at boot time), press c to get the grub prompt, and run the command
```
vbeinfo
```
to get a list of all available gfxmode settings. So for example, you may get

800x600x24

as the highest one. Then you will probably not succeed with

1024x768x24

You can also try with some boot option [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by dagring on 2013-05-21
Thanx for your answer. I have tried to do the changes in grub [ran the vbeinfo command], but it doesn't change anything. I have a Nvidia graphics card, and use the propreritary driver. I have read that this makes the startup more crappy. It seems I have to live with this.

Dag R

---

### Post by sudodus on 2013-05-21
This may be true.

---


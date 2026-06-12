---
title: "Feisty LiveCD boot problems (Black Screen)"
date: 2007-06-05
forum: General Help
---

### Post by pjman on 2007-06-05
My Feisty LiveCD will not boot. I've tried both the first option and safe graphics mode. Both show the progress bar while loading data from the CD. Once that is done the screen goes black and I hear the Ubuntu startup sound. Gnome never loads. 

I've checked messages, dmesg, Xorg.0.log and nothing stands out to me as an error message. I've tried plugging my monitor cable into the second output connector of my video card with no luck. 

What else can I try?

My hardware:

AMD Athlon 64 3500
Gigabyte GA-K8NXP-SLI
Gigabyte GV-3D1 (Dual GeForce 6600GT GPUs on one card)

Thanks

---

### Post by rapolas on 2007-06-05
How you checked your logs if you getting black screen after boot?:)

---

### Post by pjman on 2007-06-05
ctrl+alt+F1 to get a console ;)

Any ideas?

---

### Post by rapolas on 2007-06-05
You could try to make lower resolution, at least it worked for me, but I have ati video card. Lets say leave only the lowest one.```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by pjman on 2007-06-06
> **rapolas said:**
> You could try to make lower resolution, at least it worked for me, but I have ati video card. Lets say leave only the lowest one.```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thanks rapolas - that didn't fix my problem but it lead me in the right direction.

After troubleshooting I found the problem is that the LiveCD is not setting my video card's bus identifier correctly. **[SIZE="2"]It's detecting it as "PCI:4:0:0" when it should be "PCI:5:0:0"[/SIZE]**. 

My video card has two outputs (VGA and DVI). I tried changing connections thinking that was the problem with no luck.

Here are the steps I took to get Gnome running after getting the black screen at boot up:

[LIST=1]
[*]Press Ctrl+Alt+F1
[*]Type "sudo dpkg-reconfigure xserver-xorg"
[*]Choose yes to detect video card hardware
[*]Select "nv" as the drive
[*]Choose defaults until "Video card's bus identifier"
[*]Change "PCI:4:0:0" that is already populated to "PCI:5:0:0"
[*]Press  Ctrl+Alt+F7
[*]Press Ctrl+Alt+Backspace to restart X
[/LIST]

Well now I got a working Feisty LiveCD (after some modification...). Is this a bug? If so I'd like to file a bug report. Can anyone think of any other information that the developers would need to fix this problem?

---

### Post by pjman on 2007-07-01
I'm having the same problem with Gusty Gibbon Tribe 2 LiveCD. I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/119114") a few weeks ago. 

Does anyone have a Gigabyte GV-3D1 (Dual GeForce 6600GT GPUs on one card) card which works with the live CD?

---


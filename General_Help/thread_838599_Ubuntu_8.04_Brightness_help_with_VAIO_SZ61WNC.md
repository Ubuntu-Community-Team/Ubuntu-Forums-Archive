---
title: "Ubuntu 8.04 Brightness help with VAIO SZ61WN/C"
date: 2008-06-23
forum: General Help
---

### Post by H3rmaN-69 on 2008-06-23
Hi, I just installed Ubuntu 8.04 onto my VAIO laptop and the screen is on full brightness which is REALLY hurting my eyes!

Does ANYONE know how to fix this?

I have tried looking everywhere, and most places suggest replacing **[COLOR="Red"]/etc/acpi/video_brightnessup.sh[/COLOR]** and **[COLOR="Red"]/etc/acpi/video_brightnessdown.sh[/COLOR]** but it doesn't work!

I have restored the original files now.

The laptop has 2 gfx cards an NVIDIA 8400M GS and an Intel GMA x3100. I'm currently using the NVIDIA 8400M GS, but when I switch over to the Intel x3100 and reboot its still on full brightness.

Any help GREATLY appreciated!!

---

### Post by H3rmaN-69 on 2008-06-24
bump

---

### Post by Nepherte on 2008-06-24
You can adjust the screen brightness when using your intel on board vga with xbacklight:
```
sudo apt-get install xbacklight
```

You can change the brightness with: xbacklight [-help] [-display display] [-get] [-set percent] [-inc perent] [-dec percent]

As for the nvidia card, I never tried it but smartdimmer or nvclock should do it.

I documented my experiences with a Sony Vaio SZ61XN/C here: [http://bart.4aps.be/linux/ubuntu_on_a_sony_vaio_sz6.html](http://bart.4aps.be/linux/ubuntu_on_a_sony_vaio_sz6.html)

---

### Post by H3rmaN-69 on 2008-06-24
Right, I did that, and I can change the percentage, but it doesn't actually change the brightness of the screen!

Any ideas??

---

### Post by H3rmaN-69 on 2008-06-24
Right, just tried **[COLOR="Red"]xbacklight -dec 25[/COLOR]** as root and I get this...

```
[COLOR="Red"]**No outputs have backlight property**[/COLOR]
```

Any ideas?

---

### Post by Nepherte on 2008-06-24
Honestly, I don't have any idea. Xbacklight just worked for me rightaway.

---

### Post by Broken Dwarf on 2008-07-21
Bump. Did anyone come up with/ found a _working_ solution?

---

### Post by NikoC on 2008-07-21
I'm not sure if it works on your video card, but it sure did on mine (6200 Go): from the repos install nvclock via
sudo apt-get install nvclock
nvclock -S 50   --> this will reduce your brightness by 50 %
nvclock -S 75   --> this will reduce your brightness by 25 %

You can use any percentage...

Cheers.

---

### Post by wolfen69 on 2008-07-21
i'm going to ask the obvious question. did you try the keyboard method? usually Fn+F7 or F8 will change it.

---

### Post by the_fury on 2008-12-05
None of these work for me. The function keys work, and I can see the "brightness" bar decreasing steadily, but the actual screen brightness doesn't change at all. I'm running a Sony VAIO VGN-FZ240e.. 

any help?

---

### Post by Arup on 2008-12-05
Try xgamma -gamma 0.xx where xx is any value that works for you. This worked on my Viewsonic LCD monitor which was too bright at its lowest setting.

---


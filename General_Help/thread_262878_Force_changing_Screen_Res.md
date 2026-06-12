---
title: "Force changing Screen Res"
date: 2006-09-22
forum: General Help
---

### Post by noxocube on 2006-09-22
Hey all - im new to Linux...well i messed around with a Debian based Distro for a while but not long enough to call myself anywhere near competant.

The main problem im having with Ubuntu is that I can't set my resolution to my monitors native one of 1280x1024, It might be the hardware im on but i severly doubt it as like i said when messing around with DSL i managed to set my res to my monitors native one.

Anyhelp would be appreciated.

---

### Post by Henry Rayker on 2006-09-22
I had this problem too. First, you need to figure out what chipset your video adapter is using (on my laptop, it was SiS and I had this problem). You can find this in the hardware manager (I believe it's in the administration menu, but I'm at work now, so I'm not certain).

Once you know that, open a terminal and type
dpkg-reconfigure xserver-xorg

This will reconfigure xorg. When it gets to the question about your video adapter (I believe the second dialogue) make sure you select the right manufacturer...When it gets to the part where it asks for your resolutions, select the ones you want.

---

### Post by noxocube on 2006-09-22
I belive its an SIS Chipset although i'll just go check.

The thing is, I didnt want to re-format my gaming rig which is on WinXP Home so i dug around and found an old HP Pavilion N5271 with the screen ripped off (back in the days of Win M.E - must of got infuriated at such a bad OS ;P). long story short - got a splitter and now have the same monitor for my gaming rig and lappy :) and im now going to stop blabbing and start trying to find the hardware manager :P

---

### Post by Henry Rayker on 2006-09-22
let me know how it goes.

---


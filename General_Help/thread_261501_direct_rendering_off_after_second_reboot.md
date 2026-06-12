---
title: "direct rendering off after second reboot"
date: 2006-09-20
forum: General Help
---

### Post by des4ij on 2006-09-20
hey... i have ati mobility radeon 340m... followed howto for xgl+compiz for mobility radeon... after it told me to boot the first time... direct rendering was YES... and Xgl worked reall smooth and fast... but after i rebooted it again... xgl was very slow... i didnt install anything or change anything... so i tried 'glxinfo | grep rendering' and i got NO... any ideas how i can fix this... thx

---

### Post by des4ij on 2006-09-21
hello any1... i still cant fix it...

---

### Post by des4ij on 2006-09-21
Ok so just found out... direct rendering just doesnt work in xgl session... but does in gdm...  hmm... any ideas??

---

### Post by des4ij on 2006-09-21
ok so.... found another thing... changed display... i get direct rendering but then... when i start compiz with compiz-start it crashes and takes me back to login screen... any ideas?...

---

### Post by RAOF on 2006-09-22
Direct rendering **doesn't** work with XGL, pretty much by design.  That's not your problem.  Your problem is "XGL runs slowly", and I'm not sure why that is.  
You probably should provide more information, such as:
1) what graphics drivers you're using
2) what xgl/compiz packages you are using, and what versions they are.
3) any errors in your X logs (/var/log/X.0.log, etc)

You also might have better luck on the [compiz.net](compiz.net) forums.

---

### Post by des4ij on 2006-09-22
yea i realized that after i messed around with the startxgl file... if i dont start xgl i have direct rendering... well the problem is that i want to be able to run quake III in Xgl... i have it working in normal session... but glxgears is REAL slow in Xgl... i have ati radeon 340m using 'radeon' driver... thx though... i'll see wut i m able to do about it...

---


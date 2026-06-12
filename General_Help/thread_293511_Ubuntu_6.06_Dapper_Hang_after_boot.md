---
title: "Ubuntu 6.06 Dapper Hang after boot"
date: 2006-11-05
forum: General Help
---

### Post by gkasinath on 2006-11-05
Hello all, 

Lately, my ubuntu on Fujitsu C2220 has been hanging without warning. 
The last update that I did was to 'fox2.0, and the update from automatix. 

Boot is normal, login happens, I access applications and keep working and suddenly it all hangs. 
There are no messages in dmesg to indicate whats wrong. 
My guess is that the X11 has some problems after the last update, but I cant remember any updates to X11. 

Any pointers? Anyone having the same problem? 

Thanks

Cheers
Gautham Kasinath

---

### Post by John.Michael.Kane on 2006-11-05
gkasinath best bet have talk with the automatix folks since this issue happened after using their product.

If you  want to reset you xorg.conf run **sudo dpkg-reconfigure xserver-xorg**: doing so at your own risk as I don't know what modification the 3party apt has done.

---

### Post by gkasinath on 2006-11-05
Hey Plissken, 
My guess was the automatix. However, I am also inclined to think it might be an X11 server issue. 
Tell me, if X11 server crashes, then the ctrl+alt+backspace wouldnt work would it? Also the ctrl+alt+f2 wouldnt work would it? 

I will monitor the box and if this happens again, I will reconfigure xorg.conf. 

Will keep you guys posted. 

Cheers
Gautham

---

### Post by gkasinath on 2006-12-14
heads-up, I moved to edgy and havent seen this problem again. Dunno why this happened though, beats me.

---


---
title: "Make CD Ripping Faster"
date: 2006-12-12
forum: General Help
---

### Post by HokeyFry on 2006-12-12
how come in ubuntu it takes like 20 mins to rip a cd, yet in windows i can rip a cd in like 5?

and is there a way to make this go any faster?

---

### Post by mcduck on 2006-12-12
what program you are using to rip the CD's?

If it's Grip, turn off Paranoia and Extra Paranoia (these fix errors on scratched disks but make ripping slower).

If it's Sound Juicer, press alt-F2 and run 'gconf-editor', then use it to browse to apps/sound-juicer and change value for 'paranoia' to 0.

---

### Post by HokeyFry on 2006-12-13
thanks tons that helps out alot

---

### Post by HokeyFry on 2006-12-13
also is there a way to speed up cd burning?

---

### Post by mcduck on 2006-12-13
Probably. I'm using Gnomebaker and it let's you just choose the speed you want.

If you're using Nautilus to burn CD's I'm not sure. There's a setting for speed in gconf-editor (apps/nautilus-cd-burner) but the key's description doesn't tell what values it accepts. By default it seems to be 0 which I suppose means automatic, you could try to change that to something else.

---

### Post by HokeyFry on 2006-12-14
yeah umm my speed is back slow again. the first cd i ripped it ripped at 5.0x speed, but now its down to 2.0x. This is only like .5 above what it was before, does anyone have an explanation or know how to fix it again? paranoia is still set to zero, I checked it.

---

### Post by bodhi.zazen on 2006-12-14
I use K3b and have found it to be faster and more reliable. It checks md5sums fro example.

I have not looked at gnomebaker recently but in the past I had similar issues and found it made coasters at higher speeds.

HTH

---

### Post by HokeyFry on 2006-12-14
im using sound juicer. also installing a KDE program on this computer would be a hassle, as it is not connected or anywhaere near the internet. hmmm i think i may try installing gnomebaker on there though and try that

---


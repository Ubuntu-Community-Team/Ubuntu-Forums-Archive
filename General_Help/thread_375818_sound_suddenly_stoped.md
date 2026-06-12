---
title: "sound suddenly stoped"
date: 2007-03-04
forum: General Help
---

### Post by EarlGrey on 2007-03-04
Hello, I have been finally getting rid of windows, took one disk with windows out, reinstalled grub on my minulx disk, and all was fine. Only, the sound does not work any more.

Only hint I can see is that the "volme control" in the tray is not there any more. Please, could anybody help? Shoudl I put here some other specifications (in lshw, I cann see my card properly)

EdgyEft.

---

### Post by Kateikyoushi on 2007-03-04
What is the output of this ?

```
aplay -l
```

If you get your soundcard then check alsamixer probably your card is muted.

---

### Post by EarlGrey on 2007-03-04
Only part in that is Czech

**aplay -l** give me this:
```
**** Seznam PLAYBACK Hardwarových za&#345;ízení ****
karta 0: nForce2 [NVidia nForce2], za&#345;ízení 0: Intel ICH [NVidia nForce2]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 0: nForce2 [NVidia nForce2], za&#345;ízení 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
```

---

### Post by Kateikyoushi on 2007-03-04
I assume that's your soundcard so type "alsamixer" in the terminal and check whether it is muted.

---

### Post by EarlGrey on 2007-03-04
Thanks! That helped ... I have look into it before but did not understand it. Now I unmuted some that were muted and all works, thankas very much! Farewell windows O:-)

---


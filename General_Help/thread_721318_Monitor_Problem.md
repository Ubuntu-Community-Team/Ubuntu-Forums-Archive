---
title: "Monitor Problem"
date: 2008-03-11
forum: General Help
---

### Post by ascitiesburn69 on 2008-03-11
Hi is there anyway to load the default video card and/or monitor drivers using the installation cd? my problem is that i have a laptop but im using an external monitor for it because the screen on the laptop has long been broken. the back light on the laptop screen is out and when i use ubuntu i can see that the laptop screen is still on along with the external monitor. i tried to correct this and ended up basically ruining my monitor configuration because now when it boots the external screen comes up but its very glitched and i can hardly read a thing its like horizontal lines all on the screen and it looks as though it is showing about 4 screens at the same time
Please inform me how to fix this or to load the either correct drivers or to make the configuration go back to default 
Thanks in advance
-ascitiesburn69

---

### Post by kesman on 2008-03-11
You could try to boot into recovery mode and run
```

dpkg-reconfigure xserver-xorg

```

and answer with defaults if you are unsure of something.

---

### Post by ascitiesburn69 on 2008-03-11
thanks for the reply i will try that when i get home(im at school) and reply to u with the results

---


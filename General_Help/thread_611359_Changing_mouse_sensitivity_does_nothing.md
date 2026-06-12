---
title: "Changing mouse sensitivity does nothing"
date: 2007-11-12
forum: General Help
---

### Post by fearpi on 2007-11-12
From Preferences > Mouse > Motion, changing the sensitivity does nothing at all. Doesn't affect my mouse, doesn't affect my touchpad. Never did. Not since I started with Ubuntu back in Dapper. Is this slider supposed to do something? How do I change my mouse sensitivity?

---

### Post by fearpi on 2007-11-16
Just a little bump to see if anyone knows anything about this.

---

### Post by bingoUV on 2007-11-17
Does your "acceleration" drag bar do anything?

This is from xset man page. Sensitivity reflects threshold. Does it help?
```

The parameters for the mouse are 'acceleration'  and 'threshold'.  
The mouse, or whatever pointer the machine  is  connected  to,  will  
go 'acceleration'  times  as  fast when it travels more than 'threshold' 
pixels in a short time.  This way, the mouse can be used for precise 
alignment when it is  moved  slowly, yet  it  can  be  set to travel across
 the screen in a flick of the wrist when desired.

```

The sensitivity does not directly result in speed of the mouse. It is more for getting precision in mouse motion.

---

### Post by fearpi on 2007-11-17
The acceleration bar does work, yes. However, I've never wanted mouse acceleration. I hate it. What I want is simply to increase the speed.

The way that excerpt is worded, it seems possible that I could lower the threshold to nothing, so that changing the acceleration would simply change the overall speed. I'll give it a try when I'm back on my box.

---

### Post by fearpi on 2007-11-17
Well, that sort of works. The problem is that because the cursor motion is multiplied, it moves by several pixels at a time.

---

### Post by Cractuar on 2008-06-09
I don't like acceleration either and use this...

1. edit /etc/X11/xorg.conf

under the mouse InputDevice add
Option	"Sensitivity" "2.5"

where 2.5 is 2.5 times original mouse movement

2. logout,login

---

### Post by lenzoid on 2008-06-23
> **Cractuar said:**
> 
Option	"Sensitivity" "2.5"


Love this forum, love this people. I was looking for this for ages! Thanks man!

I never really understood how this accel-treshold crap actually worked and I wonder why this issue is covered extremely scarceful over the linux gaming community. Man its really tough too become good at FPSes with Maccel turned on.

---


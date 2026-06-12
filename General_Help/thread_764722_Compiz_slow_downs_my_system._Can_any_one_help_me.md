---
title: "Compiz slow downs my system. Can any one help me ?"
date: 2008-04-24
forum: General Help
---

### Post by brijith on 2008-04-24
Hai friends,


first of all let me give you an idea about my system configuration.

Motherboard: intel 915GAV
Processor  : Intel pentium 4 3GHz
Memory 	   : 1Gb + 256 Mb of RAM

I don't Have any external cards like graphics or Video

And I am running Ubuntu Gutsy 7.10 along with Compiz in it.
But when ever I enable Compiz my PC becomes slower and slower
I have to turn Compiz off to get my PC to full speed

Did any one else experience such issued ? 
Can Any body help me ?
 

[COLOR="Red"]Thanks[/COLOR]

---

### Post by justleen on 2008-04-24
i've noticed the same thing.. Just have to keep in account that all the ey candy does need CPU power, and thus can slow down your system ...

---

### Post by kpkeerthi on 2008-04-24
Your CPU is just fine. But compiz needs quite a capable GPU. The more powerful the better. Most on-board GPUs can't cope with compiz's demand.

---

### Post by vishzilla on 2008-04-24
I have almost the same motherboard Intel 915GL, but fortunately Compiz works fine on this mobo.

---

### Post by brijith on 2008-04-24
So you people saying that I have to change my system. :(

---

### Post by vishzilla on 2008-04-24
try this command ```
glxinfo | grep render
``` to see if your video card supports direct rendering. the result should be ```
direct rendering: Yes
```

---

### Post by brijith on 2008-04-24
friends,
I forgot to say something to you. Ubuntu that I had in my PC is 64Bit. Does it make any difference. My Processor is intel Pemtium 3GHz HT, I think actually it is not 64Bit but it does support 64Bit computing 

What you people think, Can I feel any difference if I install 32Bit Ubuntu Gutsy 7.10

Waiting for your valuable reply

[COLOR="Red"]Thanks[/COLOR]

---

### Post by brijith on 2008-04-24
> **vishzilla said:**
> try this command ```
glxinfo | grep render
``` to see if your video card supports direct rendering. the result should be ```
direct rendering: Yes
```

Sorry I can't try it now. Because I am at office now. I will try it when I go Home. anyway [COLOR="Red"]thanks [/COLOR]

---

### Post by vishzilla on 2008-04-24
hmmm..that makes it tricky. what does ```
uname -a
``` give out

---

### Post by vishzilla on 2008-04-24
Ok...reply once you are back home

---

### Post by justleen on 2008-04-24
direct rendering wil be Yes, since otherwise you cant enable the desktop effects?

---

### Post by brijith on 2008-04-24
> **justleen said:**
> direct rendering wil be Yes, since otherwise you cant enable the desktop effects?

I will check that 

:)[COLOR="DarkRed"] Thanks[/COLOR]

---


---
title: "HDMI turns TV ON and OFF"
date: 2019-05-03
forum: General Help
---

### Post by torbentf on 2019-05-03
Hi,
I connect my laptop w. Ubuntu via HDMI to my Sony Brava TV which I have set to HDMI input. Sometimes it works -. other times the TV comes on and goes off as the laptop does the same. When the TV comes on, the laptop goes off.
I understand that the laptop interferes with the TV, but how? And what is the remedy?
Can anyone help?
torben

---

### Post by Autodave on 2019-05-03
Can you give us some info on your system please?  What version of 'buntu are you running?  Did it ever work correctly?

---

### Post by torbentf on 2019-05-03
Hi Autodave,
I am using Ubuntu 18.04.2 LTS. Tge Sony is a 5 year old Brava. The laptop is a rather old Acer Aspire 7739G.
I bought a new HDMI cable and when I started using that everything worked fine. I could access Arte in France via Chrome.
I think the interference sneaks in via the HDMI cable because I can run the laptop and the TV simultaneously if the HDMI cable is disconnected.
torben

---

### Post by torbentf on 2019-05-03
Hi Autodave,
The HDMI cable is 1 m
torben

---

### Post by Autodave on 2019-05-03
You could always have a bad HDMI connector on the PC or the TV.  You could also have a cheap/faling HDMI cable.

What driver do you have installed for the Nvidia card and where did you get it from?

---

### Post by CatKiller on 2019-05-03
> **torbentf said:**
> other times the TV comes on and goes off as the laptop does the same. When the TV comes on, the laptop goes off.
I understand that the laptop interferes with the TV, but how?

To me, that sounds like [HDMI-CEC](https://en.wikipedia.org/wiki/Consumer_Electronics_Control).

That *can* be very useful: when I turn on my PS3, my TV turns on and switches input to it; I can control my PS3 and my NUC through my TV remote. It sounds like you're having issues with the implementation in your hardware. You should be able to control both which signals the TV sends, and how the computer responds to those signals.

---

### Post by torbentf on 2019-05-04
Hi,
It works now - I cant really say which one of a multitude of methods that I tried that did it. A friend of mine closed the lid of the computer and that certainly made a difference. But I am not sure.
Well, it appears to work and now I have to get to know it.
THank you very much
torben

---


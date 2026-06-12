---
title: "Switch from XGL to AIGLX on Edgy with ATI"
date: 2006-11-23
forum: General Help
---

### Post by hexion on 2006-11-23
Hello.

I have purchased a new monitor. It's a wide-screen one (Dell 2007WFP).

Now, I'm experiencing problems I didn't have with my other monitor, banding with movies. When a movie is in a fast scene, there are many bands blinking and it's difficult to watch it correctly.

I've realized it's a problem with XGL. With the live CD there's no problem at all, and if I start a new session without XGL it works well too. It's not a Beryl problem because running XGL with metacity still makes the problem appear.

Well, at this point I'm thinking of switching from XGL (with propietary drivers) to AIGLX using free drivers.

I've tried changing from "fglrx" to "ati" in xorg.conf and turning to "TRUE" the composite section... but it doesn't work.


Anybody can help me?
Thanks in advance.

---

### Post by RAOF on 2006-11-23
What ATI card do you have (ie: is it actually supported by the OSS drivers?).  What "doesn't work"?  Have you checked out the Beryl forums for a howto for Beryl on the ATI OSS drivers?

---

### Post by kosmic on 2006-11-23
First you need to remove xserver-xgl (search for it in synaptic)
Then you need to remove the fglrx package, and the restricted kernels.
Then  start a normal gnome sessions, and it should work :).

Also don't forget to change in your xorg.conf from "fglrx" to "ati" or Radeon.

---

### Post by JSVH on 2006-11-23
The open source ATI drivers only support up to certain cards. If yours is new you may be stuck with the proprietary drivers which don't support composite extension (which AIGLX needs).

This is the situation I am stuck in with my ATI X1400 Mobility. To new to be supported by the open source drivers, no composite extensions in the proprietary drivers, and XGL gives me trouble on other things. So no fancy desktop for me, for now :( .

---

### Post by Orval on 2006-11-24
It didn't work for me either. I reinstalled Edgy and followed [THIS]("http://ubuntuforums.org/showthread.php?t=301364") guide and now everything works great. First I had Beryl up and running using fglrx and XGL, but with the open source drivers and AIXGL it's faster and smoother. I have an ATI 9200.

---

### Post by hexion on 2006-11-24
It's a radeon 9600XT.
The problem are blinking bands with movies (banding). Whis only happens in XGL.

---

### Post by hexion on 2006-11-24
No luck here...

I did what kosmic said (thank you ;) ) but it didn't work. Well, not totally at least...
I managed to make beryl work without XGL (aiglx was there I suppose) but many things didn't work and system was unstable.

I think I'll have to try a clean install to try to make it work, or just close session and open it without xgl when I want to watch a movie :(

---


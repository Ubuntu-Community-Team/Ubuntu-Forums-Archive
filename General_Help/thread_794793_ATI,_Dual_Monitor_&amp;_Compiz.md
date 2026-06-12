---
title: "ATI, Dual Monitor &amp; Compiz?"
date: 2008-05-14
forum: General Help
---

### Post by Continuum on 2008-05-14
Hey everyone,
   After my laptop installation of Hardy went so well, I thought I would try switching my desktop to it as well. Everything works well but I would like to get Compiz working with my dual monitors.
I am currently using BigDesktop with a virtual monitor size of 2560x1024.
So, everytime I run compiz, i get this:

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 1002:4152 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

After reading a few posts, I was still unable to find a way to get this to work, but I assume the main problem is that the fglrx drivers do not allow 3D textures greater than 2048.

Is there any work arounds or fixes for this? i don't care if i continue to use the ATI drivers or bigDesktop, i just would like to have compiz and be able to drag windows from monitor to the other.

---

### Post by RAOF on 2008-05-15
> **Continuum said:**
> ...

After reading a few posts, I was still unable to find a way to get this to work, but I assume the main problem is that the fglrx drivers do not allow 3D textures greater than 2048.

Actually, I'm pretty sure this is a *hardware* limitation, so (barring crazy hacks) is not going to be solved by a change in drivers.

> **Continuum said:**
> 
Is there any work arounds or fixes for this? i don't care if i continue to use the ATI drivers or bigDesktop, i just would like to have compiz and be able to drag windows from monitor to the other.

I believe the answer to this is "no".  Although you should be able to run multiple X screens, that will mean each screen is completely separate.

---


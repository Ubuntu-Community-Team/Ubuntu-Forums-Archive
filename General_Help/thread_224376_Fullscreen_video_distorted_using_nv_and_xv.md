---
title: "Fullscreen video distorted using nv and xv"
date: 2006-07-27
forum: General Help
---

### Post by gamma on 2006-07-27
I would like to go back to using the nv driver instead of nvidia. I'm not a PC gamer and really don't have any need for GLX. I have an interesting issue where on fullscreen video the image becomes distorted. There are vertical distortion lines shooting through it. Is there a solution out there to fix this issue.

It almost looks like the frequency is set too high or something. The only time I've seen an effect similar to this is when I set an old monitor to a resolution higher than what it was capable of supporting...

---

### Post by gamma on 2006-10-01
Anyone out there with similar experiences? Or a solution? :D

---

### Post by NESFreak on 2006-10-01
edit xorg
put a # in front of GLX

rename nvidia into nv
put a # for any nvidia specific line.

NESFreak

---

### Post by gamma on 2006-10-01
Well I'm looking for a solution without resorting to the proprietary driver. I want to keep using the opensource nv driver.

---


---
title: "Compiz in VirtualBox"
date: 2008-07-01
forum: General Help
---

### Post by cowdog88 on 2008-07-01
I have a vista host with Ubuntu HH on VirtualBox and I'm trying to run compiz, but when I do the window titlebars disappear and I cant use the plugins i have enabled. Any advice?

---

### Post by soccerboy on 2008-07-01
i don't think virtual box supports compiz.  Something to do with graphics supports.

---

### Post by dje on 2008-07-01
> **soccerboy said:**
> i don't think virtual box supports compiz.  Something to do with graphics supports.

yes, no virtualisation software currently supports 3D acceleration so 3D apps like compiz fusion and games will not work

dje

---

### Post by soccerboy on 2008-07-01
i knew i had read that somewhere.  thanks for confirming.

---

### Post by sdennie on 2008-07-01
The actual graphics hardware isn't presented to the guest machine and the guest only sees a virtual graphics card.  I'm not aware of any VM software that allows you to directly access the graphics card as if it were native in the guest (I think VMware has something that attempts to do this but I don't think it actually works).

---


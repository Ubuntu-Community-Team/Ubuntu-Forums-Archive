---
title: "How do you remove the hibernate and suspend buttons"
date: 2006-12-10
forum: General Help
---

### Post by GreyBeard on 2006-12-10
Hi,

My desktop doesn't work with hibernate and suspend. Not a problem for me but I would like to remove the buttons/options from the logout/login screens so that they don't get pressed accidentally.

Thanks in advance,
GreyBeard

---

### Post by justinjstark on 2006-12-10
I believe you can remove them using gconf-editor.

/apps/gnome-power-manager/can_suspend
/apps/gnome-power-manager/can_hibernate

---

### Post by GreyBeard on 2006-12-11
justinjstark,

Thanks for putting me on the right track. I also had to set
action_button_suspend and action_button_hibernate to "nothing"

I also had to comment out the following from gdm.conf

# SuspendCommand=/usr/sbin/pmi action sleep
# HibernateCommand=/usr/sbin/pmi action hibernate

Thanks for your help,
GreyBeard

---

### Post by jko21 on 2007-01-29
Hi,

Does anyone know how to do the exact same thing in kde?

Thanks

---

### Post by SinxarKnights on 2007-01-29
> **justinjstark said:**
> I believe you can remove them using gconf-editor.

/apps/gnome-power-manager/can_suspend
/apps/gnome-power-manager/can_hibernate

Awesome. worked like a charm

---


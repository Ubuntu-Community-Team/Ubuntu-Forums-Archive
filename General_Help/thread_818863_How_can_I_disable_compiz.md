---
title: "How can I disable compiz?"
date: 2008-06-04
forum: General Help
---

### Post by alexsabree on 2008-06-04
I enabled the bicubic filter on my laptop and now I can't log in to the account that I enabled it on. Is there a way I can disable compiz and logon to that account? So then I could disable the bicubic filter?

Thanks a bunch,
Alexsabree :KS

---

### Post by Barriehie on 2008-06-04
Hello, I saw this in another post and it appears to work on this end.  I made it into a script and added it to my startups.

Barrie


```

metacity --replace &
killall compiz compiz.real

```

---

### Post by owbizi on 2008-06-04
Or just select Session -> GNOME at the logon screen and change the settings wanted.

---

### Post by alexsabree on 2008-06-04
Booting to failsafe gnome worked perfectly.. thanks man

Can't believe I forgot about that :)

---

### Post by Barriehie on 2008-06-04
> **owbizi said:**
> Or just select Session -> GNOME at the logon screen and change the settings wanted.

Ah ha!  Much better solution... :oops:

Barrie

---


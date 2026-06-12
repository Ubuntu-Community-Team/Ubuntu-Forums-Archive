---
title: "Change The Shutdown Button?"
date: 2008-06-10
forum: General Help
---

### Post by Nikayah on 2008-06-10
Is there any way to change the shutdown button? I've seen themes that do so, but can i just load in a different image?

---

### Post by Locutus_of_Borg on 2008-06-10
name whatever image you want to use "system-log-out.png" and put it in your icon theme's actions directory (/usr/share/icons/THEME_NAME/actions)

that may be all that is needed, but you may also need to make a copy of it in that directory called stock_quit.png or just link to it

```

cd /usr/share/THEME_NAME/actions
ln -s system-log-out.png stock_quit.png

```

those are the names of the icon in my theme at least.  but im using xfce

---


---
title: "No menus in evince, sometimes other programs"
date: 2013-11-25
forum: General Help
---

### Post by krytorii on 2013-11-25
For some reason the menus for certain applications are acting weird. Evince always acts like this, the file browser only seems to when I select "open containing folder" in firefox. 

Evince gives the following output when opened from the terminal:

```

$ evince
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.

(evince:5730): EvinceDocument-CRITICAL **: ev_document_get_n_pages: assertion 'EV_IS_DOCUMENT (document)' failed
```

Screenshots: 

[IMG]http://i.imgur.com/waECsUf.png?1[/IMG]

[IMG]http://i.imgur.com/rL8UVfU.png?1[/IMG]

---

### Post by bapoumba on 2013-11-25
May be here : [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/1068549](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/1068549)

Also which theme are you using ? Please try with one of the standard ones.

---

### Post by krytorii on 2013-11-25
Thank you, the .fonts.conf message is no longer appearing.

I'm using the Oxygen theme, which is one of the ones that came with kubuntu.

---

### Post by bapoumba on 2013-11-26
Glad to see you got it to work :)
Please mark your thread as solved in the Thread Tools menu.

---


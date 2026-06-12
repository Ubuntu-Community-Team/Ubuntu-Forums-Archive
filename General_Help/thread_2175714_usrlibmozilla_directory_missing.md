---
title: "usr/lib/mozilla directory missing"
date: 2013-09-20
forum: General Help
---

### Post by BigBig5 on 2013-09-20
In firefox I see no plugins and can't install any plugins. I see that my usr/lib/mozilla directory is missing. How can I get it back?:confused::confused:

---

### Post by bkline on 2013-09-20
Open a console or terminal window and enter the command:

sudo mkdir /usr/lib/mozilla

---

### Post by BigBig5 on 2013-09-20
Still non of the plugins will install.

---

### Post by Yellow Pasque on 2013-09-20
Ubuntu's package uses /usr/lib/firefox, so you never had a /usr/lib/mozilla. You should delete the extra dir you made:
```
sudo rmdir /usr/lib/mozilla
```

If you want to install plugins that aren't packaged, you put them in ~/.mozilla/plugins (.mozilla is a hidden folder and you;ll probably have to create the plugins dir inside it).

---

### Post by vasa1 on 2013-09-21
OP, how and from where did you install Firefox? What is your operating system and its version?

Ordinarily, you don't need to create any folders or do anything other than install the plugins you want. Why don't you share some more information and also mention the plugins you want.

---


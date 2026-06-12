---
title: "Empathy Online Accounts not working"
date: 2013-03-12
forum: General Help
---

### Post by CrusaderAD on 2013-03-12
When I install empathy to a fresh Xubuntu install, it says I need to setup an Account. I click on account settings and it brings up the gnome control center but no Online Account option. I run ```
gnome-control-center online-accounts
``` and add a google account, but nothing connects in chat. Any ideas?

---

### Post by CrusaderAD on 2013-03-13
Found a work around... enter this into terminal:

```
 env XDG_CURRENT_DESKTOP=GNOME gnome-control-center
```

Trick it into thinking you're in gnome I guess. Then click on online accounts and configure. Yay. Empathy works in Xubuntu now.

---


---
title: "Cannot see log off menu"
date: 2008-05-20
forum: General Help
---

### Post by Neoeyal on 2008-05-20
Hi
When I press CTRL + ALT + DELETE or the Shut Down button on the top panel it automatically logs off instead of showing the menu where you choose between several options (log off, shut down, lock screen, etc...)
How can I make it show me that menu instead of automatically log off?

Thanks,
Eyal

---

### Post by MythosLegend on 2008-05-20
Run gconf-editor.
Go to /apps/gnome-session/options.
You should have something called logout_prompt.
Make sure the box beside it is checked.

---

### Post by Neoeyal on 2008-05-21
Thank you! it works.

---


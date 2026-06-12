---
title: "Xubuntu 14.04 Can't delete unwanted menu entry from Whisker Menu"
date: 2014-11-16
forum: General Help
---

### Post by AshNova on 2014-11-16
Hello everyone,

I had installed Jamestown from Humble Bundle and then deleted the game folder as it did not come with an uninstall app/script.

Trouble is the Jamestown entry is still present in the Whisker menu and I can't delete using MenuLibre. 

[IMG]http://i.imgur.com/niaWsdH.png[/IMG]

[IMG]http://i.imgur.com/wKrxQnW.png[/IMG]

It doesn't show up in usr/share/applications either

Wondering if anyone can help me out.

Thank you.

---

### Post by Dennis N on 2014-11-16
There could be a .desktop file for the program in **~/.local/share/applications**. Delete it if there is.

---

### Post by AshNova on 2014-11-17
> **Dennis N said:**
> There could be a .desktop file for the program in **~/.local/share/applications**. Delete it if there is.

Thank you Dennis!

That did the trick.

---

### Post by Dennis N on 2014-11-17
Glad to be of help, and thanks for the feedback!

---


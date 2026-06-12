---
title: "Customizing the nautilus right-click menu"
date: 2006-10-28
forum: General Help
---

### Post by TeeAhr1 on 2006-10-28
How would I add "view hidden files" to the right-click menu in Nautilus?  The toolbar is too darn far away.

---

### Post by meng on 2006-10-28
Why not use the keyboard shortcut ctrl-H?

---

### Post by TeeAhr1 on 2006-10-28
I know, mostly just out of curiosity's sake...

---

### Post by fragos on 2006-10-28
Nautilus Scripts let you add all kinds of functionality activated through right click.  I use "Open as Administrator" frequently and find less need to go to the command line.

---

### Post by TeeAhr1 on 2006-10-29
Oooh!  Did you write that?

---

### Post by fragos on 2006-10-29
> **TeeAhr1 said:**
> Oooh!  Did you write that?

Found it on the web.  Create a text file with the following 3 lines named "Open as Administrator" and place it in your home directory in .gnome2/nautilus-scripts/

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done

---

### Post by TeeAhr1 on 2006-10-30
Bookmarking this for when I get home, thx!

-p.

---


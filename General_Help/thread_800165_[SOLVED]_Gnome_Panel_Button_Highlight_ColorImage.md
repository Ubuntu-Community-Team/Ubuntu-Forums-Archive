---
title: "[SOLVED] Gnome Panel Button Highlight Color/Image"
date: 2008-05-19
forum: General Help
---

### Post by Genius314 on 2008-05-19
[COLOR="Silver"]I'm working on my own GTK+ theme right now, and what's really bothering me is the panel buttons.
When a window in the background needs your attention (for instance, you get an IM), the button has a white rectangle drawn over it, which fades in and out.
What do I have to add to gtkrc to change this, if possible, to an image file? If not possible to make it an image, then at least change the color and size (I need it 1 pixel smaller on each side)?

Thanks.[/COLOR]

EDIT: Figured it out, if anyone cares.
Just had to add bg[SELECTED] = "#xxxxxx" to the style used for the panel.

---

### Post by Triggerhapp on 2008-12-02
Aha, thats how its done. Thankyou

---


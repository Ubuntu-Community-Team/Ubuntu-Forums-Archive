---
title: "Overlapping desktop icons - how to fix?"
date: 2006-11-28
forum: General Help
---

### Post by Shay Stephens on 2006-11-28
I am probably not the only one who experiences this, and I am hoping someone knows a fix I have overlooked.

The problem in ubuntu (gnome):
Icons on the desktop will overlap each other when a cd is loaded, a usb thumb drive, or even some new files.

I have the "Keep Aligned" setting turned on, and have to manually do the "Clean up by name" action to keep the icons from staying overlapping.  But is there a way to have the desktop keep itself cleaned up?

---

### Post by Shay Stephens on 2006-11-28
I have made one discovery.  If you want to have the text under the icons not take up so much horizontal space, use 
```
gconf-editor
```
Navigate to "apps - nautilus - icon-view" and select the "default_use_tighter_layout" checkbox.  

The text under the icons will now word wrap in a smaller amount of space.

---


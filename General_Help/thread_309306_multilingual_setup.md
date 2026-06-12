---
title: "multilingual setup"
date: 2006-11-29
forum: General Help
---

### Post by shochatd on 2006-11-29
I'm a fairly new Ubuntu user. What is the best way in Ubuntu to set up several different foreign language keyboard layouts that I can switch among to create a multilingual document? I currently have US English and Bulgarian layouts specified in my xorg.conf (I'm using the xorg.conf from my previous distro since Ubuntu was unable to come up with acceptable video settings for my monitor). Should I take the keyboard items out of xorg.conf first? I'm running 6.10 (Edgy).

---

### Post by mcduck on 2006-11-29
the easiest way is to specify layouts in Gnome's keyboard settings (as long as they have the same amount of keys) and then add Keyboard Indicator to your panel..

So, keyboard settings are in System/Preferences/Keyboard/Layouts, and to add the panel applet right-click on empty space in your panel, select 'Add to Panel', find 'Keyboard Indicator' and drag it to your panel.

---

### Post by shochatd on 2006-11-30
Thanks for your reply. I had tried that, but it had given an error message. But once I fixed my xorg.conf to *not* specify any language layouts, I was able to use the method you suggested. It seems to work now.

---


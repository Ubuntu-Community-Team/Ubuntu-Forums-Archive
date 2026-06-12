---
title: "How do i change this?"
date: 2007-04-18
forum: General Help
---

### Post by spankymasterc on 2007-04-18
how do i change the icon the ubuntu icon in left corner to this

---

### Post by bwhite82 on 2007-04-18
> sudo apt-get install gconf-editor

Then:

> sudo gconf-editor

Once you're in it, goto Apps > Panel > default_setup > objects > menubar
Double click on "custom_icon" on the right pane and enter the path to your new icon.

---


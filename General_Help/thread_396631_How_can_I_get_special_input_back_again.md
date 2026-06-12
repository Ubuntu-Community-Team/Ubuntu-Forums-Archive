---
title: "How can I get special input back again?"
date: 2007-03-29
forum: General Help
---

### Post by MysticAurora on 2007-03-29
On previous installations of Xubuntu, I was able to either hold Ctrl+Shift+hex number for a Unicode entity, or use an optional compose key that could also help me insert special characters. However, I don't have that functionality anymore and would like to get it back. How would I do that?

[EDIT] I figured out how to get Right Alt to work as a Compose key. Open a text editor and create ~/.Xmodmap. Inside it, put

```
keysym Alt_R = Multi_key
```

Then add the following line to your ~/.xinitrc:

```
xmodmap $HOME/.Xmodmap
```

After that, just hit Ctrl+Alt+Backspace to restart X and everything should be working.

---


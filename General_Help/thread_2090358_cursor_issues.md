---
title: "cursor issues"
date: 2012-12-02
forum: General Help
---

### Post by Jacob-Gates on 2012-12-02
Okay, I spent many hours trying to figure out how to change the cursor theme with no luck. I have given up but now it's all screwed up and some of the cursors are black and some are white and it's driving me nuts... how do I fix this? I have install and used galternatives, gnome tweak tool, ubuntu tweak, and dcon editor (i think that's it). Would it reset everything if I uninstall some of these? Thanks in advance.

Jacob

---

### Post by stinkeye on 2012-12-02
>  Would it reset everything if I uninstall some of these?
No. They're just tools to change configs.

Are you logging out after making changes in dconf and galternatives?


_Set back to default cursor._
Set the cursor to default in **dconf** (which is the setting various tweak tools change), using terminal...
```
gsettings set org.gnome.desktop.interface cursor-theme DMZ-White
```

then set DMZ-White in galternatives. Need to logout for the galternatives change to come into effect.

---

### Post by Jacob-Gates on 2012-12-02
> **stinkeye said:**
> No. They're just tools to change configs.

Are you logging out after making changes in dconf and galternatives?


_Set back to default cursor._
Set the cursor to default in **dconf** (which is the setting various tweak tools change), using terminal...
```
gsettings set org.gnome.desktop.interface cursor-theme DMZ-White
```

then set DMZ-White in galternatives. Need to logout for the galternatives change to come into effect.

Yes I was logging out, I even tried completely rebooting a couple of times. when I did they gsettings command you gave me its output was:
```
 ** (process:5320): WARNING **: failed to commit changes to dconf: The connection is closed
```

not really sure what to do about that.

---


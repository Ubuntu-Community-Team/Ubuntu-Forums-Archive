---
title: "Compiz and Emerald"
date: 2008-04-26
forum: General Help
---

### Post by CorruptNoob on 2008-04-26
Hi, some of my themes require Emerald as their window decorator, I'm currently having to type: emerald --replace in the terminal each session, I know there's a way of getting it to run at startup, but some of my themes don't use emerald

Is there any way of getting compiz to detect whether it needs emerald or not?

I see a Window Decoration section in Advanced Desktop Effect Settings but I'm not sure how to use it, any help would be appreciated

---

### Post by dirtblack on 2008-04-26
I fiddled around with advanced settings and couldn't find the setting I wanted for emerald.  I found some advice here about adding emerald --replace to the session manager. That works fine until a better fix comes along.

---

### Post by pro003 on 2008-04-26
did you try this?

```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra emerald
```

---

### Post by CorruptNoob on 2008-04-26
Hi I tried that

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by pro003 on 2008-04-26
that means you have already insatalled emerald and compiz...

now, go to System > Preferences > Sessions > Add 

than type Name: Emerald  >  Command: emerald --replace 

add comment if you want and save.. Exit > reboot

Before that open Emerald and import some themes .emerald which you can find at [www.gnome-look.org](www.gnome-look.org)

Good luck

---


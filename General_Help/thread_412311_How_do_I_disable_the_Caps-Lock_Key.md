---
title: "How do I disable the Caps-Lock Key?"
date: 2007-04-17
forum: General Help
---

### Post by Espreon on 2007-04-17
Please How do I do it permanently?

---

### Post by ardchoille42 on 2007-04-17
> **Espreon said:**
> Please How do I do it permanently?

I just put:

```

xmodmap -e "keysym Caps_Lock = "

```

into ~/.gnomerc and logged out and back in. Viola, no more caps lock :)

---

### Post by Espreon on 2007-04-17
Did not work, only worked during the session I input the code. I mean is there a way to automate this?
EDIT: Never Mind I crafted your code into a shell script then I made said script executable so it would load when Ubuntu loads! But thanx for the code!

---

### Post by stylishpants on 2007-04-18
An easier (or at least more gui-oriented) way is this:

Navigate through the menus:
   System->Preference->Keyboard

Select the "Layout Options" tab

Select "Ctrl key position" and choose "Make CapsLock an additional Ctrl."

---

### Post by Espreon on 2007-04-18
Uh thanx for telling me that.

---


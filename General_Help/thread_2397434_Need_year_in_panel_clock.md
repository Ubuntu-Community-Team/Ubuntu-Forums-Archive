---
title: "Need year in panel clock"
date: 2018-07-29
forum: General Help
---

### Post by raleigh3 on 2018-07-29
I want my panel clock to show the year.

 It currently only shows month and day.

Preferences has no provision for the year.

Is there a way to accomplish that. 

If not directly, is there an app I  can add to my panel that includes month,day, year?

Thanks.

---

### Post by #&amp;thj^% on 2018-07-29
If this is a Mate DE
change it dconf at <org/mate/panel/objects/clock/prefs/ custom-format> to %a %H:%M %m/%d/%Y
If you need to install it:
```
sudo apt install dconf-editor
```
Just to be clear "%Y"will add just the Year.

---

### Post by raleigh3 on 2018-07-29
I have dconf installed but do not understand how to use it?

---

### Post by #&amp;thj^% on 2018-07-29
> **raleigh3 said:**
> I have dconf installed but do not understand how to use it?

"dconf" and "dconf-editor" are different the editor is GUI instead of CLI
If this is easier just use this in the terminal:
```
dconf write /org/mate/panel/objects/clock/prefs/custom-format "'%a %H:%M %m/%d/%Y'"
```

---


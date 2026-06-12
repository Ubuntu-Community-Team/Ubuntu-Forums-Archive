---
title: "[SOLVED] possible to change main menu text color?"
date: 2008-05-01
forum: General Help
---

### Post by xecure on 2008-05-01
hi there, I was wondering if it was possible to change the color of the text in the main menu, not just the main menu but also the time and date text. I have set my main menu opacity low and it is sometimes hard for me to see my menu properly.

---

### Post by nvteighen on 2008-05-01
> **xecure said:**
> hi there, I was wondering if it was possible to change the color of the text in the main menu, not just the main menu but also the time and date text. I have set my main menu opacity low and it is sometimes hard for me to see my menu properly.

Yes, create a file named .gtkrc-2.0 (it will be a hidden file, as it starts with ".") in your home folder that includes the following code (or if it already exists, paste this to the end):
```

style "my_color"
{
fg[NORMAL] = "#E2E2E2"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

```

Change #E2E2E2 (a light grey) into something that fits better to you.

---

### Post by cubeist on 2008-05-01
Thanks nvteighen!

@ nvteighen
Do you know how to change the color of the little separators in the gnome panel?

---

### Post by xecure on 2008-05-01
btw, is it possible to change my menu height to less then 20? right click + properties doesn't let you go less then 20

---

### Post by nvteighen on 2008-05-02
> **cubeist said:**
> Thanks nvteighen!

@ nvteighen
Do you know how to change the color of the little separators in the gnome panel?

I don't know... I think it's defined by the theme you're using.

> **xecure said:**
> btw, is it possible to change my menu height to less then 20? right click + properties doesn't let you go less then 20

According to gconf-editor (open a Terminal, type gconf-editor and go to /apps/panel/objects/toplevels/bottom_panel_screen0 and search for size), minimum is based on font size and other data (?)...

---


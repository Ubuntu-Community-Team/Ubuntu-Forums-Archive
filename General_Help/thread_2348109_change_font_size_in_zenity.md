---
title: "change font size in zenity"
date: 2016-12-31
forum: General Help
---

### Post by marsdenf on 2016-12-31
Using xubuntu 14.04 and zenity version is 3.8.0  Is it possible to change the font size in a zenity info window?  Can someone give me a simple example of how to do it?  The script command I am using is:   zenity --info --text="Screensaver has been de-activated" .  I would like to increase the font size of the text.

---

### Post by sudodus on 2016-12-31
You can use Pango markup.

```
zenity --info --text="Hi <big>big guy</big>"
```

See this link: [Pango Text Attribute Markup Language](https://developer.gnome.org/pango/stable/PangoMarkupFormat.html)

---

### Post by marsdenf on 2016-12-31
Thanks.  Presumably if I want an ever bigger font, I would substitute "bigger" for "big"?

---

### Post by sudodus on 2017-01-01
You can try, but there are more details in the link from post #2. You can use the full power of the **span** construct to select font and font size.

---


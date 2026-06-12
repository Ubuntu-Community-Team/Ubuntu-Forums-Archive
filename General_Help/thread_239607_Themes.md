---
title: "Themes"
date: 2006-08-19
forum: General Help
---

### Post by Dylan103 on 2006-08-19
Ok, I have the Cobble theme by Lokheed, and I have a couple questions, I have the firefox theme and the File Edit View and such, the background is orange, is it possible to change? Its same with gaim and stuf.

And the Menu bars(bottom and top) are like grey, is it possible to change color?

[[IMG]http://img81.imageshack.us/img81/3370/screenshotmr8.png[/IMG]](http://imageshack.us)

---

### Post by IYY on 2006-08-19
Go to the theme's folder. It will most likely be something like:

```
~/.themes/ThemeName/gtk-2.0/
```

Edit the file gtkrc.

In it, there are all the colours in hex. The part you want might look like this, but it depends on the engine:

```
style "clearlooks-menu" = "clearlooks-default" {
        xthickness = 2
        ythickness = 1

        bg[NORMAL] = "#f4f1eb"
}

```

Replace the orangeish colour with any colour you like.

---


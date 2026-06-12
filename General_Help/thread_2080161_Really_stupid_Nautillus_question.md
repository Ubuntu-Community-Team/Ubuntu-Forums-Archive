---
title: "Really stupid Nautillus question"
date: 2012-11-03
forum: General Help
---

### Post by buteobuteo on 2012-11-03
Why do you have to put a Nautillus window full screen before you can see File, Edit etc?

---

### Post by howefield on 2012-11-03
Try hovering the mouse over the top panel when the window isn't maximised, you should see the menu appear.

---

### Post by Hreinsi on 2012-11-03
[QUOTE=buteobuteo;12334661]Why do you have to put a Nautillus window full screen before you can see File, Edit etc?[/QU

If you are using Unity try Put yout mouse at top of nautilus and click it see if you get menu at unity top bar

---

### Post by buteobuteo on 2012-11-03
Thanks for replies, neither work, I can only see the menus when I hover at full screen.  It's just disconcerting when you can't see them until you remember to go full screen.

---

### Post by hal8000 on 2012-11-03
Its its Ubuntu 12.10 hover over the titlebar and press "Alt" on the keyboard, that displays menu in Unity for me.

---

### Post by buteobuteo on 2012-11-03
I've got the idea now but it seems a really odd/daft thing to separate the menu bar from the program.  You could do something really disastrous if you accidentally gave the focus to the wrong program.

---

### Post by JRV on 2012-11-03
This "feature" is called global menus.
To put the menus back in the window run the following command:
```

sudo apt-get remove indicator-appmenu

```

---

### Post by buteobuteo on 2012-11-03
Thank you JRV, that did the trick, suits my simple mind a lot better.

---

### Post by grahammechanical on 2012-11-03
> it seems a really odd/daft thing to separate the menu bar from the program.

Not to the person that owns Ubuntu and to the developers that develop it. There is method in their apparent madness. It is just a different way of working. That is all.

---

### Post by buteobuteo on 2012-11-03
> **grahammechanical said:**
> Not to the person that owns Ubuntu and to the developers that develop it. There is method in their apparent madness. It is just a different way of working. That is all.
I take your point, do you know the reason for choosing this method?  To me it is counter intuitive.

---

### Post by Cheesemill on 2012-11-03
It's to maximise available screen space.

With Canonical pushing to get Ubuntu on more mobile devices (tablets and smartphones) it makes sense because screen real estate is at a premium on these types of device.

---

### Post by buteobuteo on 2012-11-04
It certainly does make sense for small devices, it might be a good idea to be able to turn it on and off easily so that for a large screen you could turn it on but have it off on your tablet/phone.

---


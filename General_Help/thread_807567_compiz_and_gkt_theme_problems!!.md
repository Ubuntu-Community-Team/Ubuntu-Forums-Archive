---
title: "compiz and gkt theme problems!!"
date: 2008-05-25
forum: General Help
---

### Post by cl0ckwork on 2008-05-25
i set up a theme for my ubuntu just using the appearance setting and getting some themes from gnome-look.com.

then i installed compiz today and it changed the look of my window borders and titlebar text.
would this be because i dont have emerald with it? or some other issue?

has anyone else had this problem?

---

### Post by jpeddicord on 2008-05-26
What version of Ubuntu are you using? If it is 7.10 or above, there is no need to install Compiz; it is already available and enabled by default.

Would you mind attaching a screenshot of your problem? Press PrintScreen on your keyboard to take a screenshot, and save it to your desktop. Reply to this post, and hit Manage Attachments to upload your screenshot.

---

### Post by Forlong on 2008-05-26
Sound like you do have Emerald installed/enabled.

Run this via [Alt]+[F2] ```
gtk-window-decorator --replace
```

---

### Post by cl0ckwork on 2008-05-26
didnt know that compiz was already installed,but heres the screenshots i took.  the first one is what it looks like now, the second is what my actual theme should look like.

and forlong i ran the script but i didnt notice any difference

---

### Post by Forlong on 2008-05-26
Ah, why didn't you add the screenshot before, that expains it all.

You are using gtk-window-decorator already but with the generic theme.
Run this in the terminal:
```
gconftool-2 -s -t bool /apps/gwd/use_metacity_theme true
```

---


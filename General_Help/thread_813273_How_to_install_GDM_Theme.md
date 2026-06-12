---
title: "How to install GDM Theme?"
date: 2008-05-30
forum: General Help
---

### Post by Old Marcus on 2008-05-30
I've downloaded a GDM theme from gnome-look and yet I don't seem to be able to do much with it. system>administration>login screen.local gives me an add button, but it can't see the theme?

---

### Post by pmaconi on 2008-05-30
Did you try adding it without removing it from the archive? You can also try and drag-n-drop the archive into the selection window in the login screen browser.

---

### Post by Old Marcus on 2008-05-30
The archive was .rar, and the login manager couldn't see it. :S

Edit: sorted. saved the rar as a tar.gz

---

### Post by ShodanjoDM on 2008-05-30
To install GDM theme:

System>>Administration>>Login Window

It is a system-wide theme, so you must enter your password.

Click on the "local" tab, and you can see other installed themes. Drag&drop the downloaded GDM tar file there.

EDIT: Oops, my bad. I didn't notice there's already an answer.

Ok, extract the .rar and move the folder to /usr/share/gdm/themes/ either with Nautilus in root/admin mode or terminal:

```
sudo mv <the name of the gdm theme> /usr/share/gdm/themes/
```

If you want to use Nautilus instead, press Alt+F2 and type 

```
gksudo nautilus /usr/share/gdm/themes/
```

Then copy-paste or move the new GDM theme there.

---


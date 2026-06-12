---
title: "How to hide Dash to dock in Menu Applications"
date: 2021-03-23
forum: General Help
---

### Post by datlechin on 2021-03-23
How to hide dash to dock on the left side of the applications menu

thanks

[ATTACH=CONFIG]288175[/ATTACH]

---

### Post by tea for one on 2021-03-23
Dash to Dock is an extension rather than an application.

You either have them active or inactive via [COLOR="#0000FF"]gnome-tweaks[/COLOR]

---

### Post by slickymaster on 2021-03-23
@datlechin

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by deadflowr on 2021-03-23
Remove dash-to-dock.
Ubuntu already has dash-to-dock, called Ubuntu-dock.

(Note, you may need to logout and back in again for the removal change to take affect)


Also, fwiw,
A difference between them is dash-to-dock has settings controls available in gnome-tweaks.
(Ubuntu Dock does not have a settings option in gnome-tweaks)

But Ubuntu dock can be configured using gsettings/dconf/dconf-editor.
So if you want to customize the look and feel you can use dconf editor and go to
org > gnome > shell > extensions > dash-to-dock
and set the various options however you like.

---

### Post by kurt18947 on 2021-03-23
Dash to Dock is one of my must-haves. I access it via the extensions.gnome.org web site. Select "installed extensions" from the ribbon near the top of the screen. You should see Dash to Dock listed. Click on the little screwdriver and wrench icon, that should open a new window. In the "position and size" I have "intelligent autohide" selected. There is further customization available by clicking on the little gear very near the "intelligent autohide" slider. I had to intentionally break the default Ubuntu launcher, I had both launchers appearing and it was confusing.

---


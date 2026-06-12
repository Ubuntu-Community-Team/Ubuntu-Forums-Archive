---
title: "Anyone know of an Xubuntu icon theme with blue folders?"
date: 2021-05-28
forum: General Help
---

### Post by dontknowwhattonamethis on 2021-05-28
The title isn't very descriptive, because I didn't want it to go on too long.
I like the elementary XFCE icons in Xubuntu.  But I don't like the tan folder icons which interfere with the blue accents.  I found an icon set which has blue folders but it uses the old icons for other apps so it's very inconsistent.
So, basically is there a modification of the elementary xfce icons with blue folders? Or can I add the blue folders which I took from the other theme into thunar?

---

### Post by tea for one on 2021-05-28
Alternatively, you could consider Papirus Icons with a facility to choose various folder colours.

[https://github.com/PapirusDevelopmentTeam/papirus-folders](https://github.com/PapirusDevelopmentTeam/papirus-folders)

---

### Post by &amp;KyT$0P# on 2021-05-28
You can override individual icons in a theme.

Create the folder [FONT=Courier New]~/.local/share/icons/elementary-xfce[/FONT]
For every place there is a tan folder icon in [FONT=Courier New]/usr/share/icons/elementary-xfce[/FONT] , put a corresponding blue folder icon in [FONT=Courier New]~/.local/share/icons/elementary-xfce[/FONT] .  For example, there is [FONT=Courier New]/usr/share/icons/elementary-xfce/places/32/folder.png[/FONT] , you would need to put a 32x32 png of a blue folder at [FONT=Courier New]~/.local/share/icons/elementary-xfce/places/32/folder.png[/FONT] .  Repeat for all folder icons.

(The elementary-xfce icon theme that came with Xubuntu 18.04 had blue folder icons.  You can download it [here]("https://packages.ubuntu.com/bionic/xubuntu-icon-theme").  I wouldn't recommend installing that package on newer Xubuntu, but you can extract its contents and use the icons to override as described.)

---


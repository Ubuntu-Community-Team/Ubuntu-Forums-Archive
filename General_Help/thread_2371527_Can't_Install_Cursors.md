---
title: "Can't Install Cursors"
date: 2017-09-15
forum: General Help
---

### Post by mrgnome on 2017-09-15
Title says it all. I am simply unable to install cursors. When I put them into the .icons folder, they don't show up in the Tweak Tool.

---

### Post by speartip on 2017-09-15
The cursor folder needs to be put in /usr/share/icons, not in HOME/.icons.

---

### Post by again? on 2017-09-15
$HOME/.icons works here on Ubuntu-Gnome 17.04 and Unity 16.04.
What distro release are you using?
If you link to a theme, I can test.

Check you're putting the right folder in ~/.icons
Some downloaded cursors come with multiple themes that also need to be extracted.
When you open the folder you're placing in ~/.icons you should see an **index.theme** file and a "cursors" folder similar to attached pic.

In previous releases you needed the index.theme file to link to alternatives but it appears this is not used now
and after selecting the theme in gnome-tweak-tool you just need to logout or reload gnome-shell to complete the change.

---


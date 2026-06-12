---
title: "fonts.conf: Modifications does nothing :-|"
date: 2020-08-24
forum: General Help
---

### Post by dinkidonk on 2020-08-24
I have been trying to make some font settings in "~/.config/fontconfig/fonts.conf", based on various info found ( [LINK]("https://manpages.ubuntu.com/manpages/artful/man5/fonts-conf.5.html") [LINK]("https://askubuntu.com/questions/32727/how-do-i-turn-off-font-pixel-antialiasing-only-in-terminal") ), but whatever I do the modifications does not show up. As a test, I have added an alias to another existing font with:

```
<alias>
  <family>Glorious</family>
  <prefer><family>FreeMono</family></prefer>
  <default><family>FreeMono</family></default>
</alias>
```

But it apparently does nothing. I have found info about a missing inclusion in "/etc/fonts/fonts.conf", so I have added:

```
<include ignore_missing="yes" prefix="xdg">fontconfig/fonts.conf</include>
```

To make sure that the file under ~ is loaded - this does not change anything either.

Ever since I have made these changes, the "Fonts" page in "System settings" is always in a modified state which wants to be either saved or discarded - even if nothing is modified.

Any help on this?

Kubuntu 20.04.1 fully updated.

EDIT: I have tried "fc-cache", of course. I have also tried to search for my alias with "fc-match", which always finds something but not the alias.

---

### Post by GhX6GZMB on 2020-08-24
First, avoid using "~" in any situation other than a direct shell command. Only bash or sh (or some other shells) will expand the "~" character. Use $HOME instead, this always works.

running **sudo fc-cache -f** ought to update your fonts, but apparently doesn't, which is strange. I've no idea why.

---


---
title: "Irie Menu / Mint Menu"
date: 2008-05-20
forum: General Help
---

### Post by swisscow on 2008-05-20
Love using this menu in Mint, but would prefer to use it in Ubuntu, however doesn't seem to work. Sub Menus don't seem to have any applications in them or I can't open them at all, there are "empty" icons in the menu and right clicking and choosing preferences or edit menu brings up nothing of help.

Anyone got any ideas how to make this work?

---

### Post by swisscow on 2008-05-21
Found out a solution

Added the mint repositories, quoted below, then ```
sudo apt-get update
```, ```
sudo apt-get install mintmenu
```

```
# +++ Elyssa (Linux Mint 5) +++
deb http://packages.linuxmint.com elyssa main upstream import
## deb http://packages.linuxmint.com elyssa community
## deb http://packages.linuxmint.com elyssa backport

## +++ Romeo (Linux Mint Unstable) +++
deb http://packages.linuxmint.com romeo elyssa

## +++ Source Repositories +++
deb-src http://packages.linuxmint.com elyssa main upstream import
## deb-src http://packages.linuxmint.com elyssa community
## deb-src http://packages.linuxmint.com elyssa backport
deb-src http://packages.linuxmint.com romeo elyssa
```

Not sure if this is overkill but hasn't seemed to cause any problems.

Has added the Elyssa menu (Mint beta) which has an interesting feature - right clicking on an application gives you the opportunity to uninstall the application - seems to work as well!

Have to say, I prefer this menu to the others I have tried, seems more intuitive, and less clicks required than others. Personal view of course

---


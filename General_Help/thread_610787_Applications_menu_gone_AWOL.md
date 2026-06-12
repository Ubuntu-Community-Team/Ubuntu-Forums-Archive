---
title: "Applications menu gone AWOL"
date: 2007-11-12
forum: General Help
---

### Post by Duroon on 2007-11-12
I seem to have lost my applications menu. I still have the system tools menus but when I click on applications nothing. I have tried starting the menu editor but it won't start up. I am not sure if the menu definitions file is messed up or even where it is stored on my system actually. My guess is that this is what has happened though. Anyone able to help me out?

---

### Post by JasonF on 2007-11-12
Try removing the directories '~/.config/menus' '~/.local/share/applications', and '~/.local/share/desktop-directories'. This will undo any user specific changes to the menu, but should hopefully get it to work again.

---

### Post by Duroon on 2007-11-12
> **JasonF said:**
> Try removing the directories '~/.config/menus' '~/.local/share/applications', and '~/.local/share/desktop-directories'. This will undo any user specific changes to the menu, but should hopefully get it to work again.

I got into .local/share/applications and there was a menu editor in there. I ran it and set the menu back to defaults and it reappeared. I went back in and started editing again and as soon as I edited some choices under the Internet menu the applications menu's disappeared again. So I hit defaults once more and bingo all back again. One of those choices under Internet is doing it but I don't understand how or why.

---


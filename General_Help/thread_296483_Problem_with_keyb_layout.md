---
title: "Problem with keyb layout"
date: 2006-11-09
forum: General Help
---

### Post by extasy on 2006-11-09
Hi,

I have a problem with my keyb settings in Gnome can't use alt gr key this results in me not beeing able to use <at> . This is the results I get doing:
xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "sv", "sv", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "sv", "sv", "lv3:ralt_switch"
henrik@henrik-ubuntu:~$ 

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [sv  sv,se]
 model = pc105
 options = [lv3 lv3:ralt_switch,eurosign        eurosign:e,grp  grp:alts_toggle]
 overrideSettings = true

Anyone who can help me, I have a 106key keyboard

Best regards
Henrik

---

### Post by ozorba on 2006-11-10
Here is another problem with a keyboard. I am using Kubuntu and when I tried to change to a different layout it did not work. I tried to check if everything is correct in Settings-> Regional & Accessibility-> Keyboard Layout and ticked Enable keyboard Layouts I got nothing in Keyboard Model.

I swear it was there after I first installed Kubuntu Edgy and set it up.

---


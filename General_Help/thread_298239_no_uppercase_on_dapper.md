---
title: "no uppercase on dapper"
date: 2006-11-12
forum: General Help
---

### Post by jlm on 2006-11-12
hello all,

i'm on dapper now and i have a problem with my second user : i cannot write uppercase letters nor use the delete key ! ](*,)  i have no problem with my main user

i tried to change the keybord properties (ie the layout), i had an error message saying to look at xprop -root | grep XKB and gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd :

here the results : 


xprop -root | grep XKB

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "fr", "FR", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "fr", "FR", ""



gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

** (process:7796): WARNING **: Owner of /tmp/orbit-lulu2 is not the current user
 layouts = [fr  FR,us,latam]
 model =
 options = [grp grp:alts_toggle]
 overrideSettings = true

help me !


jl

---


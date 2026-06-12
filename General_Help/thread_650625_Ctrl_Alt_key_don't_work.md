---
title: "Ctrl Alt key don't work"
date: 2007-12-26
forum: General Help
---

### Post by cedric_l on 2007-12-26
Hi,
     I have a french keyboard , Logitech Internet Cordless Pro and another basic keyboard , and with none of these I succeed to use alt and Ctrl keys.
 I'am using ubuntu.7-10 and the kernel is 
2.6.22-14-generic .

 I tried to set the problem via the desktop panel through Preferences/keyboard/Layout and Layout Options

 In layout I chose "France Other, with no dead keys" 
 and in layout options , I chose " any alt key selects the third level "

 after this settings, I saw displayed the following message :

  XKB configuration activation error ...
 the end of the message give me the advice of running the following commands : 
  xprop -root | grep XKB
  gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

  here are the results :
 
 cedric@lachez-moi:~$ xprop -root | grep XKB
  _XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "fr", "latin-9", "lv3:ralt_switch"
  _XKB_RULES_NAMES(STRING) = "xorg", "pc105", "fr", "latin-9", "lv3:ralt_switch

 and

   cedric@lachez-moi:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
    layouts = [fr  latin-9]
    model =
    options = [lv3 lv3:ralt_switch,grp     grp:alts_toggle,lv3     lv3:alt_switch]
    overrideSettings = true


  Has anybody an idea that would prevent me from doing 
 copy and paste of @ for a long while :)

  Thanks

---


---
title: "xorg language setting fails in httpS firefox input ?"
date: 2006-07-29
forum: General Help
---

### Post by videodrome on 2006-07-29
Hello. I am confused and I really need help please. I have this in my xorg.conf file in xubuntu to make it dvorak. Both alt keys turn it on and off:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "dvorak,us"
        Option          "XkbOptions"    "grp:alts_toggle,grp_led:scroll"

Note that it works great everywhere in X and on the Web.

EXCEPT when in Firefox I go to a secure site like ebay and have to enter my 
password in. Then it fails. I can't see what's actually going on, because the browser just shows asterisks when one is typing their password.

When I switch to qwerty and enter my password it works correctly.

What is going on here? 

Thanks!

---


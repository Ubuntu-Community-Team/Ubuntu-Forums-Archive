---
title: "Can't enter @ \ and so on with keyboard"
date: 2007-05-21
forum: General Help
---

### Post by FizzBuntu on 2007-05-21
That's strange one that I didn't notice but it seems that I can't use the chars I should have with the alt gr key (~#{[|`\^@]} and so on)
I've set a french keyb and reinstalled it - same
tried the keyboard on other computer - works perfectly....

---

### Post by bapoumba on 2007-05-21
Hi,
did you choose the generic 105-key (intl) layout ?

---

### Post by FizzBuntu on 2007-05-21
yes, it was automaticaly chosen...

---

### Post by bapoumba on 2007-05-21
French keyboard and layout here. Here is the relevant section of /etc/X11/xorg.conf :
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbOptions"    "lv3:ralt_switch, compose:rwin"
EndSection

```

---

### Post by FizzBuntu on 2007-05-22
ok, the good news is that it works
the bad news is that it wasn't the keyboard setting that werent' good, it's the user profile that has a problem.
Something with the .drmc file avoiding saving parameters in it. That's bad news because of course I don't care much about using an other user profile but I hve many things in my profile (mail, icq, etc.)
Is there a way to "regenerate" the .drmc file or to import setting from a profile to another ?

---

### Post by FizzBuntu on 2007-05-22
ok, don't  bother, i've fixed it.
thx

---

### Post by bapoumba on 2007-05-22
> **FizzBuntu said:**
> ok, don't  bother, i've fixed it.
thx
Did you change the permissions on .drmc back to your user? (just so that if other members have the same problem and read your thread, they will know how you fixed it). Thanks.

---

### Post by FizzBuntu on 2007-05-23
no, in fact i've made a backup of the user's home directory - delete the user, then recreate it and import some data files like the .mozilla directory.
I also add to change owner and group of the imported file 'cause when you delete the user, it's own by 1000.
After that, everything works great (even my other post concerning nx bandwidth usage).
This solution isn't perfect for sure 'cause I add to reconfigure all the shortcuts and preferences, but still, it works...

---


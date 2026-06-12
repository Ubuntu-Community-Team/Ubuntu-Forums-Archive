---
title: "Terminal colors"
date: 2014-08-16
forum: General Help
---

### Post by Imperium Guard on 2014-08-16
Hi, my name is Harvey and i'm new to the forums ):P- just have a question:

After enabling color in ~/.bashrc, by uncommenting force_color_prompt=yes, the color isn't working.

This is my PS1 variable: ```
if [ "$color_prompt" = yes ]; then    PS1='$HC$FGRN${debian_chroot:+($debian_chroot)}\u@\h:$FCYN\w\$ $RS '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

HC is high color, FGRN is foreground green, and FCYN is foreground cyan.
Does bash support this feature or did I mess something up?

---

### Post by vasa1 on 2014-08-16
> **hduongd said:**
> Hi, my name is Harvey and i'm new to the forums ):P- just have a question:

After enabling color in ~/.bashrc, by uncommenting force_color_prompt=yes, the color isn't working.

This is my PS1 variable: ```
if [ "$color_prompt" = yes ]; then    PS1='$HC$FGRN${debian_chroot:+($debian_chroot)}\u@\h:$FCYN\w\$ $RS '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

HC is high color, FGRN is foreground green, and FCYN is foreground cyan.
Does bash support this feature or did I mess something up?

Hi, I didn't need to uncomment "**force_color_prompt=yes**".

Nor did I modify **PS1** the way you have. I left it as it was. Instead, I just added a last line to my .bashrc:```
PS1="\[\033[31m\][\@]\[\033[31m\] \w $ \[\033[0m\]"
```.

---

### Post by Imperium Guard on 2014-08-16
Yep, I replaced the variables with the direct code, and it worked, thank you! :p

---


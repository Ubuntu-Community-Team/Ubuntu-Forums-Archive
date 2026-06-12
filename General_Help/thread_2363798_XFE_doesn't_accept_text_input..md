---
title: "XFE doesn't accept text input."
date: 2017-06-14
forum: General Help
---

### Post by jan-80 on 2017-06-14
Hello,

I have the same problem as described in :
[https://ubuntuforums.org/showthread.php?t=2235440](https://ubuntuforums.org/showthread.php?t=2235440)
XFE does not accept text input.

The solution provided in that thread won't work for me.

From the above thread I learned that 'purging' ibus (whatever that is) is a solution to the problem.
From the above I also learned that ibus is the system component to allow foreign characters. I do need that, because I'm working on a Belgian AZERTY keyboard, to be able to write accented characters in my languages (Dutch and French) It's not very likely that I'll ever use these in a file- or directory-name, but if purging ibus breaks the keyboard driver for accented characters like éèà or specials like çµ£, systemwide, I can't have it.


I'd like to use XFE, but if I can't get it to input text, it's useless. So if my problem can't be solved, You can propose alternatives. ;-)


System:
Dell Inspiron 15 (3552) pre-loaded with Ubuntu
Ubuntu 14.04.02 LTS 


Regards,
Jan-80

---

### Post by jan-80 on 2017-06-15
[SIZE=2][FONT=courier new]I just went ahead and tried something else that was mentioned: [COLOR=#000000]System Settings > Language Support > Keyboard Input Method System > From IBUS to None. 
After a reboot I could:
- still use all special and accented characters in GEDIT
- create folder names in XFE

So this worked and problem solved.
Thanks to all who contributed! ;-)

Greetings from the TyRannoSaurus
Jan-80 [/COLOR][/FONT][/SIZE]

---


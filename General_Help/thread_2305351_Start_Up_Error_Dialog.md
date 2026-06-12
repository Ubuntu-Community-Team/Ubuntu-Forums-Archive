---
title: "Start Up Error Dialog"
date: 2015-12-05
forum: General Help
---

### Post by moebob24 on 2015-12-05
Getting this 3 times in a row upon boot with zero detail...

[http://i.imgur.com/TEfszeu.png](http://i.imgur.com/TEfszeu.png)

System runs just fine though.

What should I be looking for and what log would something like this go to?

---

### Post by deadflowr on 2015-12-05
Look in /var/crash.
Most likely the crash report system being trigger-happy.

You can turn in off by disabing apport
open /etc/default/apport as root(sudo) in a text editor
and change the line that reads enabled=1 to enabled=0
and save.

---

### Post by moebob24 on 2015-12-05
> **deadflowr said:**
> Look in /var/crash.
Most likely the crash report system being trigger-happy.

You can turn in off by disabing apport
open /etc/default/apport as root(sudo) in a text editor
and change the line that reads enabled=1 to enabled=0
and save.

Making that edit did work. Now I'm curious, I did a little digging (notes and findings below), what does ***/usr/share/apport*** do and is this tied to this path? EDIT: By this path I mean ***/etc/default/apport***

Does this setting impact real crash report situations?

**[SIZE=6]Side tangent![/SIZE]**
**I also found a few reports:**
Can you talk to me about the naming syntax? I recognize the date string in the top one as something I was fiddling with in Python earlier, but what about the others? One came from my user account too. (Bottom, I stared it out).

The Xorg log has quite a bit in there as well.

```

root  whoopsie    40210 Dec  5 08:13 susres.2015-12-05_08:13:28.815735.crash
root  whoopsie 26546795 Dec  5 12:48 _usr_bin_Xorg.0.crash
***** whoopsie   685392 Dec  5 17:29 _usr_lib_x86_64-linux-gnu_indicator-keyboard-service.1000.crash

```

---


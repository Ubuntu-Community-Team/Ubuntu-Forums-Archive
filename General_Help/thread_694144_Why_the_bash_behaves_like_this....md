---
title: "Why the bash behaves like this..."
date: 2008-02-11
forum: General Help
---

### Post by Nevermore on 2008-02-11
Hello
I found out that when i try to send this command in a script:
 gksu "mkdir -p /usr/share/locale/${3%%.*}/LC_MESSAGES ; msgfmt ${2} -o /usr/share/locale/${3%%.*}/LC_MESSAGES/$1.mo"

it ends up with an error..
if i change ; with &&
i still get an error
the only way to make it work is to split into two commands
gksu "mkdir -p /usr/share/locale/${3%%.*}/LC_MESSAGES"
gksu " msgfmt ${2} -o /usr/share/locale/${3%%.*}/LC_MESSAGES/$1.mo"

I can't find why this is happening and truly talking is a bit annoying, because this script works perfectly in Debian..
Is there something i should correct to make the bash behave like in debian?
Thanks

---

### Post by yabbadabbadont on 2008-02-11
The default shell in Ubuntu is Dash, not Bash.  Make sure that your script uses Bash.
```
#!/usr/bin/env bash
```
Should be the first line of the script.

---

### Post by Rocket2DMn on 2008-02-11
I'm not going to try and analyze that command, but you have it in quotes with gksu on the outside, have you considered:
```
gksu "mkdir -p /usr/share/locale/${3%%.*}/LC_MESSAGES" ; gksu "msgfmt ${2} -o /usr/share/locale/${3%%.*}/LC_MESSAGES/$1.mo"
```

---

### Post by Nevermore on 2008-02-12
> **Rocket2DMn said:**
> I'm not going to try and analyze that command, but you have it in quotes with gksu on the outside, have you considered:
```
gksu "mkdir -p /usr/share/locale/${3%%.*}/LC_MESSAGES" ; gksu "msgfmt ${2} -o /usr/share/locale/${3%%.*}/LC_MESSAGES/$1.mo"
```

yes i did this
but truly talking i don't see why it is working on debian and not in ubuntu..
this makes me think that some bash specification have been changed in ubuntu, and i would like to know which ones..
btw
the script starts with #!/bin/bash so is not the case..

---

### Post by Rocket2DMn on 2008-02-12
If it works in Debian, perhaps it's a difference in bash version or gksu functionality.

---

### Post by Keith Hedger on 2008-02-12
```
gksu "mkdir -p /usr/share/locale/${3%%.*}/LC_MESSAGES ; msgfmt ${2} -o /usr/share/locale/${3%%.*}/LC_MESSAGES/$1.mo"
```
giving an error is correct as the semi-colon just allows you to put two commands on one line, with the above the 1st command is run with root priviliges(gksu) the second command is run without root priviliges which the command would seem to need so the line should read ```
gksu "mkdir -p /usr/share/locale/${3%%.*}/LC_MESSAGES ; sudo msgfmt ${2} -o /usr/share/locale/${3%%.*}/LC_MESSAGES/$1.mo"
```
to give the second command root priviliges , I would say this is a bug in debians bash as the second command seems to be getting root privileges without being asked for them this could be potentialy very serious!

---


---
title: "powerbtn.sh"
date: 2005-07-21
forum: General Help
---

### Post by Uthren on 2005-07-21
I'm attempting to rewrite the default powerbtn.sh script, in order to have it display the gnome shutdown menu when pressed.

```
if ps -Af | grep -q '[k]desktop' && test -f /usr/bin/dcop
then
    dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
else
    gnome-session-save --kill
fi
``` 

I have this code currently, but it doesn't seem to do anything when I press the power button...

---


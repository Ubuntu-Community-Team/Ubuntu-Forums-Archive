---
title: "how to activate monitor from stand-by using a script"
date: 2008-05-06
forum: General Help
---

### Post by franganghi on 2008-05-06
I need to activate the monitor from the stand-by status using a script.
I'm searching for the right syntax as "gnome-screensaver-command -l" is the right one to lock the screen with the default screensaver.

:(

---

### Post by sdennie on 2008-05-06
To disable standby, I think:

```

xset dpms force on

```

To disable the screensaver (almost certainly won't work if it's locked):

```

gnome-screensaver-command -p

```

---


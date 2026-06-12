---
title: "[SOLVED] Gnome-session-properties read only ? [Resolved]"
date: 2006-12-20
forum: General Help
---

### Post by El_Matthews on 2006-12-20
Gents

It seems that what ever change I make to "Gnome-session-properties/start-up programs" isn't remembered. I tried to add a script to start compiz and every time I restart the entry disappears from the list.

Just to be sure I disabled the entry nm-applet and here the same thing happens, after boot this line was enabled again(nm-applet isn't finding any network but I will start another post for that) .


Please help me troubleshoot this issue.

Thank you

Matthieu

---

### Post by jrib on 2006-12-20
Might be a permission problem.

Check the ownership of ~/.config/autostart/ and run this command (as your user) to search for anything in your home that isn't owned by you:

```
find ~ ! -user $USER -exec ls -ld '{}' \;
```

---

### Post by El_Matthews on 2006-12-20
_Jason

that's a command that I will remember.

Indeed file permissions where incorrect on the autostart directory. changed ownership from root to my user and everything works fine now.

many thanks

Matthieu

---

### Post by RAdams on 2007-02-08
Wow. Perfect. This fixes a good half-dozen problems I've had. Thanks.

---


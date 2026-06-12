---
title: "[SOLVED] Disable Hibernation?"
date: 2008-06-02
forum: General Help
---

### Post by solidsnake204 on 2008-06-02
I know that if you hibernate Ubuntu using Wubi it will corrupt the data.
I want to avoid that (eg. accidently clicking the Hibernate button).

Is there a way of disabling the hibernation like in Windows?

---

### Post by BlueSkyNIS on 2008-06-02
Press ALT-F2, type gconf-editor, in left pane browse to apps->gnome-power-manager->general. In right part of the window uncheck can_hibernate and can_suspend options


Cheers

---

### Post by ago on 2008-06-02
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/224697](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/224697)

---

### Post by solidsnake204 on 2008-06-02
Thanks BlueSky, that worked!

---


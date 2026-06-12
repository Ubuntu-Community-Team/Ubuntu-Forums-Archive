---
title: "Resume from suspend without password?"
date: 2007-12-27
forum: General Help
---

### Post by Bungtung on 2007-12-27
I am using Ubuntu 7.10 as the sole OS on a HP-Compaq nx6120 laptop.  I am the only user and use suspend often (suspend works well for me after resolving uid/sda/hda problems).

I want to be able to resume from suspend without having to input a password.  I have looked at previous threads on this issue (pre 7.10) which suggest tweaking the gnome-power-manager section of gconf-editor.

Ok, so I opened the gnome-power-manager section of gconf-editor and made sure that there were no checks in any of the "lock screen" boxes.  This has made no difference, a password is still required when I resume from suspend.

Any ideas?:confused:

---

### Post by glennric on 2007-12-27
To disable the screen locking on resume edit the file /etc/default/acpi-support
Change the line
```
LOCK_SCREEN=true
```
to
```
LOCK_SCREEN=false
```

---

### Post by Bungtung on 2007-12-28
Tried you suggestion.  I also tried commenting out the statement.  No effect at all.

Confused.

---

### Post by Bungtung on 2007-12-28
Sorry!  There was an effect.

I went back and checked that I had successfully changed and saved the statement in /etc/default/acpi-support to LOCK_SCREEN=false.  I had.  So I looked in the gnome-power-manager section of gconf-editor again and what did I find?  The lock screen boxes were now all checked!  I unchecked them and then tried suspend.  **Problem solved**.

Many thanks for your help.

---

### Post by texadactyl on 2008-06-14
Thanks for the gconf-editor note.  Worked for me too.

The desktop folks need a better human interface to take care of both the desktop level and the ACPI level in a single operation to ensure consistency.

---


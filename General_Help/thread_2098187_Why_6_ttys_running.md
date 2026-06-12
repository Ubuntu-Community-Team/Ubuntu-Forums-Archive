---
title: "Why 6 ttys running?"
date: 2012-12-25
forum: General Help
---

### Post by daKoolaid on 2012-12-25
[FONT=FreeSans]I do a cold boot but System Monitor shows 6 tty processes. Why is this? Is it safe to disable 2-6?[/FONT][FONT=FreeSans][/FONT]
[FONT=FreeSans]Thanks in advance![/FONT]

---

### Post by snowpine on 2012-12-25
What is the harm? :)

---

### Post by MishaX2 on 2012-12-25
You probably can, I don't see why though. They are so incredibly small... disabling them will save you around 100kb of memory.

---

### Post by daKoolaid on 2012-12-26
Ok. So this is not a security risk to have them running? Then I have no problem leaving it alone.

---

### Post by chadk5utc on 2012-12-26
> **daKoolaid said:**
> Ok. So this is not a security risk to have them running? Then I have no problem leaving it alone.

try running this in terminal
> ps -e | grep tty
my output is here
> # ps -e | grep tty
 1116 tty7     00:01:06 Xorg
 1654 tty1     00:00:00 agetty


This will give you some idea what each one is for

---

### Post by rnerwein on 2012-12-26
> **daKoolaid said:**
> [FONT=FreeSans]I do a cold boot but System Monitor shows 6 tty processes. Why is this? Is it safe to disable 2-6?[/FONT]
[FONT=FreeSans]Thanks in advance![/FONT]
hi
i presume it's save to reduce the number of getty processes in /etc/console-setup.
you have to change: ACTIVE_CONSOLES="/dev/tty[1-6]" to your behavior.
but i can't guarantee that lightdm will notice this "F1-F6". just give it a try.
i hope it's not hard coded anywhere.
no risk no fun  ;-)
cheers

---

### Post by Kirk Schnable on 2012-12-26
> **daKoolaid said:**
> Ok. So this is not a security risk to have them running? Then I have no problem leaving it alone.

No more or less of a security risk than having a login screen...

---


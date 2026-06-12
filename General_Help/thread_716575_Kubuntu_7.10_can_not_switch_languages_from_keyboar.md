---
title: "Kubuntu 7.10 can not switch languages from keyboard"
date: 2008-03-06
forum: General Help
---

### Post by itb402 on 2008-03-06
[SIZE="4"]I do not know how to switch input from English to Arabic in my keyboard.
I have Arabic and English languages  both are working right but I am not able to switch from keyboard.[/SIZE]

---

### Post by itb402 on 2008-03-06
???:confused::(

---

### Post by itb402 on 2008-03-08
n XFree86 prior to version 4.3.0 non-latin layouts mutually included latin group and this group was the default thus pressing Ctrl+Alt+k always yielded the right combination. From version 4.3.0 by default all layouts contain only one group thus non-latin layouts may not work here.
Possible solutions are:

add your layout to $nonlatin or $oldlayouts lists in /etc/X11/xkb/rules/xfree86 or the location of the xkb rules on your computer.

Change the shortcut to something language neutral, e.g. Ctrl+Menu

Turn on the option to include the “us” group in your layout (effectively the same as first solution

---


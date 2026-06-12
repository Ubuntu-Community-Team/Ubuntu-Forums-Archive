---
title: "where is programme"
date: 2007-08-21
forum: General Help
---

### Post by heracles on 2007-08-21
Have just installed cdlabelgen via synaptics and it says it is installed but where? It does not appear anywhere in desktop menus?. help please desparate

---

### Post by heimo on 2007-08-21
> **heracles said:**
> Have just installed cdlabelgen via synaptics and it says it is installed but where? It does not appear anywhere in desktop menus?. help please desparate

It probably lacks proper files to add itself to menu. You can try launching it by hitting alt+F2 and typing: cdlabelgen

You can then make a new launcher (shortcut) for it.

---

### Post by forestpixie on 2007-08-21
try running from the terminal

and that :)

---

### Post by jethro10 on 2007-08-21
Both of the above comments are true.

However sometimes the word you type at the terminal may not be known, ie. the program name.

I usually search for it again in synaptic, highlight it, then click on properties. Here a tab called "Installed Files" will list every file installed!

Often near the top, there are files installed in /usr/bin/ and these are most likely the name your looking for.
sometimes you need to look further.

In this instance it is :-
/usr/bin/cdlabelgen

as /usr/bin is in your path, just type cdlabelgen
To create a shortcut, right click your desktop and crate from there.
Hope this educates you some.

Jeff

---

### Post by luisromangz on 2007-08-21
You can always look in Synaptic's package properties, there you can find the files the package installed, so you can check the name of the executable one.

---


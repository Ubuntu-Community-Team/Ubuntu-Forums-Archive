---
title: "Plugins not working in Konqueror"
date: 2007-11-28
forum: General Help
---

### Post by Fibonacci on 2007-11-28
After upgrading to Gutsy, none of the plugins I'm using on Firefox is working on Konqueror (and yes, I do have konqueror-nsplugins installed). Some examples:
· When loading any site that uses Flash, a grey box appears where the animation should be.
· When clicking on a link to an audio file, I am offered the options of downloading or opening said file with an external app, instead of playing it with the MPlayer plugin.
None of those problems is present in Firefox.

How can I make the plugins work for Konqueror?

Thanks in advance,

-Fibo

(edit: the Java plugin not working was my fault)

---

### Post by Fibonacci on 2007-11-29
I just discovered that Java was disabled on Konqueror, re-enabled it, and it's working fine. I apologise for my stupidity.
This, however, does not help with Flash.

---

### Post by sageb1 on 2008-01-10
settings: configure konqueror
plugins: netscape plugins settings

search for new plugins.

---

### Post by Fibonacci on 2008-01-10
> **sageb1 said:**
> settings: configure konqueror
plugins: netscape plugins settings

search for new plugins.

Tried that. Still nothing.

---

### Post by sageb1 on 2008-01-24
have you backed up .xsession-errors in your $HOME to .xsession-errors and gone to a site that uses these plugins to get errors?

that procedure would work like this:

shell to bash using gnome-terminal

execute following command from prompt:
cp .xsession-errors .xsession-errors.backup

run Konqueror and go to site that needs those plugins - this will require clicking on multimedia if need be

then go back to the gnome-terminal and execute:
diff .xsession-errors .xsession-errors.backup

redirect the diff to a file if it's long.

what errors does a site that uses those plugins look like? oh, and what version of flash is it? 7 or 9+?

---

### Post by Fibonacci on 2008-01-24
> **sageb1 said:**
> have you backed up .xsession-errors in your $HOME to .xsession-errors and gone to a site that uses these plugins to get errors?

that procedure would work like this:

shell to bash using gnome-terminal

execute following command from prompt:
cp .xsession-errors .xsession-errors.backup

run Konqueror and go to site that needs those plugins - this will require clicking on multimedia if need be

then go back to the gnome-terminal and execute:
diff .xsession-errors .xsession-errors.backup

redirect the diff to a file if it's long.

No output is produced.

---


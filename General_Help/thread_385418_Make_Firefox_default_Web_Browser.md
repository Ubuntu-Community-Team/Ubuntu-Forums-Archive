---
title: "Make Firefox default Web Browser"
date: 2007-03-15
forum: General Help
---

### Post by gavinjb on 2007-03-15
Hi,

I am trying to make Firefox my default browser in KDE, does anyone know how to do this.

I have tried going to kcontrol/kde components/default applications/web browser and setting firefox in here.  But as soon as I click on a link in Thunderbird for instance Konqueror Opens (I tried re starting X, incase it only applies after a restart)

Thanks,


Gavin,

---

### Post by Moe70 on 2007-03-15
Did you try to make firefox your default from firefox options under 'system default'...'check now'

---

### Post by gavinjb on 2007-03-15
no, but I have just tried, and it didn't work. :(

---

### Post by Bosonator on 2007-04-29
Found a solution!

1. Open Thunderbird
2. Open this menu: Edit>Preferences>Advanced>Config Editor
3. Find the entries *network.protocol-handler.app.http* and *network.protocol-handler.app.https* by typing into the "filter" field.
4. One at a time, double click on the values for each field to change them. They probably read something like *x-www-browser* or something like that. Change them to read */usr/bin/firefox*
5. Close the config editor, and away you go.

Cheers,
Josh

---


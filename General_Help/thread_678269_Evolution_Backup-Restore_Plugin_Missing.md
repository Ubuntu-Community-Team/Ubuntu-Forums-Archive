---
title: "Evolution Backup-Restore Plugin Missing"
date: 2008-01-25
forum: General Help
---

### Post by stefangachter on 2008-01-25
For some reason, the back-restore plugin does not appear in evolution, even though the evolution-plugins-experimental_2.12.1 packages is installed.

I have no clue what is wrong with my evolution installation. Plenty of other plugins appear in the menu Edit->Plugin. 

If somebody has an idea, would be great. Thanks!

---

### Post by Flymo on 2008-04-23
Hello Stefan

We too seem to lack the 'settings backup/restore' in Evolution 2.6.1 running on Ubuntu 6.06 LTS (fully updated).

Now that we are trying to migrate to a more recent Ubuntu - maybe 8.04 - this is becoming more important, since the alternatives are a bit flaky in our experience.

There's a page here:
 [https://answers.launchpad.net/ubuntu/+source/evolution/+question/5749](https://answers.launchpad.net/ubuntu/+source/evolution/+question/5749)

...which offers some help - but from experience we know that it's not always 100% successful. :confused: 

What does work is to copy your email folders (the link describes where to find them) into your new desktop and then import them via your new Evolution.   And then update all the connections by hand.... :(

Paradoxically, the 2.12.0 version on our Gutsy installations seem to be later than 2.6.1 and include the backup/restore - something to do with Ximian/Novell version numbering vs Gnome? Not sure. Certainly implies that there may be some plugin compatibility issues awaiting the unwary.

Good luck, anyway.  Will post again if we find anything useful.

Anybody else with experience of these problems?

All the best, Ben

---

### Post by dcstar on 2008-04-23
> **Flymo said:**
> 
........
Paradoxically, the 2.12.0 version on our Gutsy installations seem to be later than 2.6.1 and include the backup/restore - something to do with Ximian/Novell version numbering vs Gnome? Not sure. Certainly implies that there may be some plugin compatibility issues awaiting the unwary.

Good luck, anyway.  Will post again if we find anything useful.

Anybody else with experience of these problems?

All the best, Ben

2.12 is obviously later than 2.6, so where is the "paradox"?

The backup works fine in 2.12.1 (Gutsy).

---

### Post by 4walters on 2008-06-21
try installing the "evolution-plugins" package

---

### Post by Flymo on 2008-06-23
Greetings, and thanks for the help.

Yes, 2.12 is obviously later than 2.6, must have had a senior moment :lolflag:

We had to do it that weekend, so a brute force folder copy and reconfigure by hand did the trick.   Suspect that installing the plugins as suggested would have done a better job! 

Thanks again, folks.  Ben

---


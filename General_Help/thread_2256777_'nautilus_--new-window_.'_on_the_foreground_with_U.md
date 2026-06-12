---
title: "'nautilus --new-window .' on the foreground with Unity."
date: 2014-12-14
forum: General Help
---

### Post by deragon on 2014-12-14
When I call on the command line (cli) 'nautilus --new-window .', Nautilus is launched in a new window, but the window does not show up in the foreground.  It remains behind other Windows.  Is there an option I can add to get the newly created Nautilus window show up above all other Windows?

Is there a GTK/Gnome option that would do this for any Gnome application?

Best regards & Thanks in advance,
Hans Deragon

---

### Post by mc4man on 2014-12-14
In an ubuntu session (unity) I find that some remaining focus issues are resolved by setting the "Focus Prevention Level" to off.
(- have yet to see a downside when doing so.
Available in ccsm (compizconfig-settings-manager) > General Options > Focus & Raise Behavior as in screen
You could give it a try & see

---

### Post by deragon on 2014-12-15
You found the solution, thank you.  Now the question that beg to be asked:  Why is that not the default setting in Ubuntu 14.04 LTS Trusty Thar (and probably later version)?  Should I report this as a bug or wish?

---

### Post by mc4man on 2014-12-16
> **deragon said:**
> You found the solution, thank you.  Now the question that beg to be asked:  Why is that not the default setting in Ubuntu 14.04 LTS Trusty Thar (and probably later version)?  Should I report this as a bug or wish?
Well focus issues of recent history (last 18 months or so) have been dealt with on an individual basis so some do remain. This change in compiz options seems to resolve the rest here & don't see a downside though maybe the setting of low has some value?

Any way filed on the setting with 2 examples of wrong behavior when the setting is at the default. 
If you have any other examples do add. (filed on 15.04 as better to do these things on current dev

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1403140](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1403140)

---

### Post by deragon on 2014-12-19
Thanks for the bug report; I joined in and confirmed it.  I encourage anyone reading this thread and agreeing to what is being discussed to add themselves in those affected by the bug report.

---


---
title: "Reinstall Unity after Gnome 3.12"
date: 2014-06-17
forum: General Help
---

### Post by kanishkdudeja on 2014-06-17
I had installed Gnome 3.12 from the PPA.

But as soon as i installed Gnome, i could not see the option to login into my unity desktop from the login screen.

How can i install Unity again? I wouldn't want to remove Gnome. Want to keep both the options available.

---

### Post by grumblebum2 on 2014-06-17
> **kanishkdudeja said:**
> I had installed Gnome 3.12 from the PPA.

But as soon as i installed Gnome, i could not see the option to login into my unity desktop from the login screen.

How can i install Unity again? I wouldn't want to remove Gnome. Want to keep both the options available.
```
sudo apt-get install ubuntu-desktop
```
What ppa did you use?
Purge the ppa if necessary.
You will still have gnome-shell...just not the gnome3-staging versions.

---

### Post by kanishkdudeja on 2014-06-17
I followed instructions from:

[http://www.omgubuntu.co.uk/2014/05/upgrade-gnome-3-12-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/05/upgrade-gnome-3-12-ubuntu-14-04)

---

### Post by grumblebum2 on 2014-06-17
Purge instructions are at bottom of that page.
To purge a ppa it must still be enabled.

---

### Post by kanishkdudeja on 2014-06-17
Purged the PPA and installed ubuntu-desktop.

Now i just see a black screen. :(

---

### Post by grumblebum2 on 2014-06-17
Do you get to the login screen?

There is a warning on that ppa...
> === *WARNING* ===
 The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

If they break your system, you get to keep both halves.

Nothing much I can say really.
If your going to add testing ppas you should have a good knowledge of how to restore when breakage occurs.

---

### Post by kanishkdudeja on 2014-06-17
Nopes, i don't reach the login screen.

I just see the Gnome Boot Screen and then a blank screen.

---

### Post by kansasnoob on 2014-06-17
I think the only thing you can do is perform a fresh install. The gnome teams PPA's are intended for use in Ubuntu GNOME, ***not Ubuntu***!

---


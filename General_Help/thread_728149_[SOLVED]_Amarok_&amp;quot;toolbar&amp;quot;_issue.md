---
title: "[SOLVED] Amarok &amp;quot;toolbar&amp;quot; issue"
date: 2008-03-18
forum: General Help
---

### Post by johntinsley on 2008-03-18
I'm not sure whether this is an Amarok problem or an Ubuntu issue so I'll try anyways.

Using Amarok 1.4.7 in gutsy gibbon the toolbar which displays the options "Engage, Playlist, etc." is permanently at the top of the screen. Even when I resize the Amarok window, the toolbar, which should be part of the Amarok window, remains detached at the top of the screen.

I've include 2 screenshots, one of how it looks (toolbar_bad) and one of how it should look (toolbar_good). Anyone have any suggestions?

Thanks,

---

### Post by forestpixie on 2008-03-18
How did you manage to get a good and bad one? Are they from different users?

---

### Post by johntinsley on 2008-03-18
One is my machine at home and the other is in work. Same distro and settings on both

---

### Post by forestpixie on 2008-03-18
Oh - was hoping you had different users. I'd say that if it's only amarok doing it that there was something wrong with a configuration file. 

You could try reinstalling it after a purge - but also delete the hidden folder, in mine it's at /home/*user*/.kde/share/apps - delete that before you uninstall then

sudo apt-get remove --purge  amarok &&sudo apt-get install amarok

---

### Post by forestpixie on 2008-03-18
been to the amarok forum - found one exactly the same - unfortunately it was EXACTLY the same :) - alos see that you've tried reinstalling, but did you delete the hidden folder last time.

---

### Post by johntinsley on 2008-03-18
hehe, yeah I posted over there first.
I didn't delete the amarok folder for the reinstall. I was hoping to avoid having to do that - so that I wouldn't lose all the track counts etc. - but I guess I'm going to have to bite the bullet and try it.

---

### Post by johntinsley on 2008-03-18
Tried what you suggested, no joy. It's quite peculiar

---

### Post by forestpixie on 2008-03-19
have you tried hiding the menu and unhiding - can't think of anything else

Edit - you could try changing themes see if that does it

---

### Post by johntinsley on 2008-03-19
Is there a way to hide that particular menu? I haven't seen the option. I tried different themes also to no effect. Curiously I saw it happen with another KDE app so I checked to see the behaviour in a KDE session and it was the same... Leads me to believe it may be something to do with this

---

### Post by Lord Illidan on 2008-03-19
Look at my screenshot. Did you enable the Mac OS style?

---

### Post by forestpixie on 2008-03-19
> Is there a way to hide that particular menu?

sorry meant menu :oops:

I think Lord Illidan is probable on the right track - if you've uninstalled, purged and deleted the hidden folder then I odn't think it's amarok - especially if other kde apps are doing similar.

If you're not running kubuntu - you can install kcontrol

---

### Post by johntinsley on 2008-03-19
Sorted! Yeah the Mac OS style was enabled, that was it. Thanks for your help guys, cheers.

---


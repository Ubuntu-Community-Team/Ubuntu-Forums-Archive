---
title: "Install KDE login screen after un-installing GNOME?"
date: 2004-11-03
forum: General Help
---

### Post by stodge on 2004-11-03
I installed KDE and subsequently removed GNOME. Now I lost the login screen, so it automatically goes into run level 3 instead of 5. How do I setup the KDE login screen instead?

Thanks

---

### Post by TekMate on 2004-11-03
[QUOTE=stodge]I installed KDE and subsequently removed GNOME. Now I lost the login screen, so it automatically goes into run level 3 instead of 5. How do I setup the KDE login screen instead?

Thanks[/QUOTE]
 Try apt-get install kdm

---

### Post by stodge on 2004-11-03
It was already installed. I rebooted and now I get kdm but KDE won't start. I have no window manager at all - HELP! :)

---

### Post by stodge on 2004-11-03
Never mind - I just re-installed gdm and I'm ok again. I'd rather not have any GNOME libraries installed, but there you go. :)

---

### Post by josel on 2004-11-03
Hmmm.... Ubuntu is gnome centric and the tools are gnome/gtk based so you'll probably end in problems some day.
Im also a kde guy and a bit disapointed that a newer kde and koffice etc are at hand.

---

### Post by az on 2004-11-03
At a root terminal, try
dpkg-reconfigure kdm
and pick kdm as your default manager.

---

### Post by ~zoey~ on 2004-11-06
If I understand this thread correctly, I can uninstall gnome safely and still be able to log in to kde as long as I have gdm installed?

Is this correct?

Thanks, zoey    :-k

---


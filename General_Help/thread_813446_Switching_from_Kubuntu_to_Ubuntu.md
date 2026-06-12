---
title: "Switching from Kubuntu to Ubuntu"
date: 2008-05-30
forum: General Help
---

### Post by avianbc on 2008-05-30
I installed Kubuntu 8.04 and used it for about 6 months now but I wanted to switch over and use Gnome instead. I installed ubuntu-desktop via apt-get and I now use this and never use my old kde installation. Can I remove all the KDE apps and the KDE desktop by typing sudo apt-get remove kubuntu-desktop? Or would it be easier to just do a fresh install?

Whats the best way for me to make the switch? All responses (good and bad) are appreciated.

---

### Post by LaRoza on 2008-05-30
> **avianbc said:**
> I installed Kubuntu 8.04 and used it for about 6 months now but I wanted to switch over and use Gnome instead. I installed ubuntu-desktop via apt-get and I now use this and never use my old kde installation. Can I remove all the KDE apps and the KDE desktop by typing sudo apt-get remove kubuntu-desktop? Or would it be easier to just do a fresh install?

Whats the best way for me to make the switch? All responses (good and bad) are appreciated.

You can use:

```

sudo tasksel

```

And uncheck what you don't want (probably be the easiest).

However, run:

```

sudo dpkg-reconfigure kdm

```

And select "gdm" as the default first.

---

### Post by latna on 2008-05-30
Removing kubuntu-desktop won't do much. It's really a kind of "meta" package that brings in all the kde stuff with it. You could try removing kubuntu-desktop and then running:

```
sudo apt-get -s autoremove
```

Make sure you don't forget the -s for simulate. You want to see what it will remove before you actually do it. I've had mixed results with that command though. I also suspect it might not work if you installed kubuntu from CD. It's worth a shot anyway.

---

### Post by avianbc on 2008-05-30
tasksel worked like a charm. Many thanks.

---


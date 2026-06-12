---
title: "login / logout sounds"
date: 2007-10-02
forum: General Help
---

### Post by meimato on 2007-10-02
I recently upgraded from Feisty to Gutsy beta and I lost my login and logout sounds.
Everything else works fine: I can regularly play music, see videos... but there's no sounds when GDM screen appears, gnome desktop loads, the session closes.

---

### Post by por100pre1 on 2007-10-02
Try this:

```
sudo aptitude reinstall ubuntu-sounds
```

You can also try [downloading]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ubuntu-sounds") the package, extract it to get the sound files, and set the system to use the sounds with:

```
gnome-sound-properties
```

---

### Post by meimato on 2007-10-07
Sorry for the delay, I couldn't check before.
I made what you wrote, but with no luck: still no sounds.
If I launch gnome-sound-properties the login and logout sounds are correctly listed, and they works if I plays them; in fact - as I said - all sounds works flawlessy: the only times I can't hear anything are when:
- GDM loads the welcome screen
- I login my gnome session
- I logout my gnome session

Thanks

---

### Post by por100pre1 on 2007-10-07
This issue is quite common. Try this:

```
gksu /usr/sbin/gdmsetup
```

Under the **Accessibility** tab there are settings for login and logout sounds, use these sounds:

/usr/share/sounds/logout.wav
/usr/share/sounds/login.wav

give them a try. Hope this helps. :)

---

### Post by meimato on 2007-10-09
Well, it seems that with the latest updates they partly solved my problem: now I hear gdm and login sounds, while I still cannot hear logout sound... waiting for the next bunch of updates, then!

---

### Post by FuturePilot on 2007-10-09
ESD, which is responsible for the system sounds, has been removed in Gutsy. The plan is to eventually replace it with PulseAudio.

---


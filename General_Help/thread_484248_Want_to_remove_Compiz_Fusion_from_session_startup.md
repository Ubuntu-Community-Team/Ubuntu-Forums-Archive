---
title: "Want to remove Compiz Fusion from session startup"
date: 2007-06-25
forum: General Help
---

### Post by Depressed Man on 2007-06-25
I added it to the session startup (after testing it for a while to see if it worked). Heh..not a great idea as I no longer have a shell when I get into the desktop. Even using gnome and gnome failsafe won't work, it just shows that color (can't describe it really..peach?) and a mouse cursor. How do I remove compiz fusion from the session startup? Thanks!

---

### Post by Brucevdk on 2007-06-25
Switch to another terminal (CTRL + ALT + F1), login and navigate to *~/.config/autostart*, remove the compiz desktop file. Most likely the following command will do the trick:
```

rm ~/.config/autostart/*compiz*

```

---

### Post by ubukool on 2007-06-25
Hi, I had exactly the same problem as you, compiz-fusion broke my system.  I've now happily gone back to using Beryl which is fantastic with no problems.  With compiz, I just got the orange screen of death and a cursor!

I went into a failsafe session and actually removed compiz completely with these commands:

sudo apt-get remove compiz  # compiz-gnome
sudo apt-get remove compizconfig-settings-manager # compizconfig-backends-* ?!
sudo apt-get remove compiz-fusion-*

(basically, the opposite of the installation guide)

When I rebooted, everything worked fine again.....phew! ;)

Good luck.   I look forward to the time when I'll be able to use compiz-fusion without such problems because it does have some awesome new features.  Beryl is great though, too :D

---

### Post by Depressed Man on 2007-06-25
> **Brucevdk said:**
> Switch to another terminal (CTRL + ALT + F1), login and navigate to *~/.config/autostart*, remove the compiz desktop file. Most likely the following command will do the trick:
```

rm ~/.config/autostart/*compiz*

```

thanks I'll try that and report back.

Compiz Fusion does work for me..but it seems not at startup. It seems fine when I load it up after I get into the desktop (which is what I did before).

---

### Post by nphx on 2007-06-25
How do you usually start compiz, with **compize --replace** right?

Just add that to System > Preferences > Sessions > click New >  name it Compiz Fusion > in command put **compiz --replace** > click OK.

Next time you boot you should have it startup automatically.

---

### Post by Depressed Man on 2007-06-25
Yeah, that&#347; what got me into this situation to begin with. Anyway, thanks! I can get back into the shell now. From now I&#314;l just manually launch compiz fusion till it gets farther along.

---


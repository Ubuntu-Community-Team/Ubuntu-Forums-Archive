---
title: "[SOLVED] Gah, Screensaver EMERGENCY - screensaver location??"
date: 2008-01-03
forum: General Help
---

### Post by Syndacate on 2008-01-03
It's exactly what the title says - where are the screensavers located?  I need to delete the actual file.

There's this stupid one that accidently got selected called "braid" - Normally I wouldn't mind, but every time my computer views this screen saver that's it - cooked - fried - locked - never to be open again - it needs to be restarted.

This means:
- My computer can't idle
- I sure as hell can't lock it
- I can't change it either

As soon as I try to change it, it sees this screen saver in the preview, and that's it, time for a restart, no keys do anything, absolute lock-up.

How the hell do I delete this stupid screen saver or change it through the command line?  As I need to be able to work my computer without shutting it down whenever I step away.

---

### Post by Syndacate on 2008-01-03
Gah, got it fixed

Fix:
Go to:
```

~/home/*user*/.gconf/apps/gnome-screensaver

```

Then type:
```

sudo kedit %gconf.xml &

```

Change the 7th line down, in between the **"string value"** tags, put **none** - so it looks like:
```

<stringvalue>none</stringvalue>

```

Opposed to:
```

<stringvalue>screensavers-glknots</stringvalue>

```

Then save.

This will select your screensaver to nothing - from the quick look around I had it seems as though I'm not the only one to have this problem, that a few different people had it with a few different screensavers.

So change it back to blank, then you can edit it through the regular **System >> Preferences >> Screensavers**.  

I'm still looking to delete that one, though, anybody know where the screensaver files are located?

---

### Post by Shrav on 2008-01-25
> **Syndacate said:**
> Gah, got it fixed
I'm still looking to delete that one, though, anybody know where the screensaver files are located?

/usr/share/applications/screensavers/

I had to delete Braid because it would lock my system (either when it was chosen by the random screen saver or if I scrolled through them in the screen saver chooser).

---

### Post by PinkFloyd102489 on 2008-01-25
I use Flurry, so im fine. :-P

---

### Post by Syndacate on 2008-01-25
> **Shrav said:**
> /usr/share/applications/screensavers/

I had to delete Braid because it would lock my system (either when it was chosen by the random screen saver or if I scrolled through them in the screen saver chooser).

Yup, I had the same exact problems.

Thanks for the path, I just deleted it.

---

### Post by tuebinger on 2008-03-01
I just removed xlyap from my screensavers file.  That was screwing up my computer no end!

---

### Post by Syndacate on 2008-03-03
> **tuebinger said:**
> I just removed xlyap from my screensavers file.  That was screwing up my computer no end!

Yeah, some of those screensavers just have a reaction like mentos and diet coke.

---

### Post by PowerlessRacing on 2008-03-10
Thank you.  This helped very much.  Everybody else is recommending upgrading the distribution or replacing the desktop.  I knew everything in ubuntu was done with configuration files, but it was tough to find out where the file was.  You fixed that for me.  :)

---


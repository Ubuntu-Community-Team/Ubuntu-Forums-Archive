---
title: "Evolution Mail &quot;The session does not exist&quot;"
date: 2020-11-27
forum: General Help
---

### Post by NertSkull on 2020-11-27
I installed evolution mail, and things were working for a few days.  I restarted my computer today and now all my mail/calendars do not connect.  I get error messages saying things like:

Failed to connected "myemail@gmail.com"
The session does not exist

Error while performing operation.
Failed to authenticate:: The session does not exist

And similar messages. I couldn't figured it out.  So I deleted all the evolution config files in .cache/evolution and .config/evolution and .local/share/evolution.

I then re-added one of my gmail accounts.  And same messages/errors.  

What happened?  And how can I fix it?

I'm on kubunut 20.04.01 and everything is updated.  And passwords or anything else have not changed.

---

### Post by timgreen2 on 2021-03-11
I have been plagued by the same problems and decided to try to figure this out.  From what I can tell in my investigations, this problem seems to stem from KDE not unlocking the necessary key rings (or the gnome-keyring-daemon is not running yet) before evolution launches and then tries to use them.  If you are requested to unlock a keyring when starting up evolution, this is possibly the cause of the issue you face.

gnome based apps like the keyring and evolution communicate over dbus, and I believe the keyring daemon will be started up by the dbus the first time evolution requests the keyring it needs.  However, evolution does not seem to handle this case and will report errors: "failed to connect" "the session does not exist".  I believe the session it's referring to is possibly the connection to the keyring daemon.

I have not yet solved unlocking the keyring before evolution starts, but if you start evolution and get the errors, then you can run: 

```
evolution --force-shutdown
```

This will shut down all of the evolution daemons, including the one that cannot reconnect to the now started/unlocked keyring service.  Then, start evolution normally, and everything should be OK.

---

### Post by NertSkull on 2021-05-13
> **timgreen2 said:**
> this problem seems to stem from KDE not unlocking the necessary key rings (or the gnome-keyring-daemon is not running yet) before evolution launches 

Yeah I'm pretty sure that's the problem, or something related.

I've solved my issue with a workaround by disabling the KDE wallet.  I don't use it.  And when I turned it off/disabled it, and then re-installed evolution and set up accounts, everything has worked smoothly since then for many months now.  

If you need the KDE wallet, then I have no clue.

---


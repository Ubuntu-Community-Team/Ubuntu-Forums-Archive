---
title: "update-manager icon never shows when updates - gusty"
date: 2008-01-17
forum: General Help
---

### Post by ture_atlantis on 2008-01-17
i have update-manager running, but it never shows up when updates are available.

process running:
```

atlantis@atlantis-laptop:~$ ps -A|grep upd
 5753 ?        00:00:00 update-notifier

```

Administration->Software Sources, Updates tab shows to check for updates daily, with download updates in the background selected...

Is there something that im missing?  Thanks.

---

### Post by ThrobbingBrain66 on 2008-01-17
Do you have the Notification Area on one of your panels?  If not, the update-manager icon won't show.  Right-click a panel, choose 'Add to panel...' find Notification Area (in the Utilities section) and click Add.

---

### Post by dcstar on 2008-01-17
> **ture_atlantis said:**
> i have update-manager running, but it never shows up when updates are available.

process running:
```

atlantis@atlantis-laptop:~$ ps -A|grep upd
 5753 ?        00:00:00 update-notifier

```

Administration->Software Sources, Updates tab shows to check for updates daily, with download updates in the background selected...

Is there something that im missing?  Thanks.

Check your settings: Synaptic-Settings-Distribution, the top box should be selected.

---

### Post by ture_atlantis on 2008-01-18
yes, the notification area is displayed...


> **dcstar said:**
> Check your settings: Synaptic-Settings-Distribution, the top box should be selected.

when you say synaptic-settings-distribution, i assume you mean the settings->properties menu of synaptic application, on the distribution tab?

if so, yes, the 'always prefer the highest version' is selected.

---

### Post by groggyboy on 2008-01-20
how are you able to tell that you have updates?  it's been my experience that synaptic and apt-get/aptitude will have updates available for a while before update-notifier picks up on them.  what happens if you wait for a bit?

---

### Post by Anduu on 2008-01-20
I suggest the same thing....

I ***know*** my Update Notifier works however the odd time I do an apt-get update/upgrade there are upgrades available but  the notifier just hasn't checked yet.

---

### Post by ture_atlantis on 2008-01-27
I know its not working because I can go to 
System->administration->update manager

and 'check for updates' and it will show there are some.  the first time i did it, there were about 200...

---

### Post by groggyboy on 2008-01-30
is update notifier set as a startup program?  ie, is it listed in system > preferences > sessions?  if not, add it (name = update notifier, command = update-notifier)

**EDIT**: i just reread your first post.  i'm guessing that my suggestion is irrelevant.

so how about this instead: in system>administration>software sources, go to the updates tab.  change the option at the bottom from "download all updates in the background" to "only notify about available updates".  maybe that'll make the icon start appearing in the notification tray.

---


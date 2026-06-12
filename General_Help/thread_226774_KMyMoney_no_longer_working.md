---
title: "KMyMoney no longer working"
date: 2006-07-31
forum: General Help
---

### Post by tonyr1988 on 2006-07-31
I love KMyMoney because  it's simpler than GnuCash - I don't need anything fancy. However, when I had to re-install Ubuntu from scratch (I messed up), it won't run anymore. I installed it from Synaptic, just like last time.

When I start it, it says:

> There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not open network socket

Please check that the "dcopserver" program is running.

I click OK, and then it pops up again. I click OK a second time, and then it says:

> Will not save configuration.

Configuration file "/home/tony/.kde/share/config/kmymoney2rc" not writable.

Configuration file "/home/tony/.kde/share/config/kdeglobals" not writable.

Please contact your system administrator.

I click OK, see the splash screen, the program comes up, and then it freezes. I try to close, and must do a force quit.

Then, I did the obvious: I opened up a terminal and typed "dcopserver" to get it started. I didn't have to do this before, but it's not a big deal.

When re-loading KMyMoney, I still get the "configuration" error, and then, after it loads the program, another errors pops up, saying:

> Could not find mime type

application/octet-stream

When I click OK, the little "home" screen instead says:

> An error occurred while loading file:///usr/share/apps/kmymoney2/html/home.html:

Could not start process

Unable to create io-slave: Permission denied

But I no longer have to force quit - it will exit normally.

Any ideas?

---

### Post by tonyr1988 on 2006-07-31
Weird....running it in sudo works perfectly (so far)

Should I just change it in Alacarte to "sudo kmymoney2" instead of just "kmymoney2"? Will that have any security risks or anything? It shouldn't, should it?

---

### Post by FenrisAbraxas on 2006-07-31
probably a ```

sudo chown tony:tony /home/tony/.kde/share/config/kmymoney2rc
sudo chown tony:tony /home/tony/.kde/share/config/kdeglobals

```

should do the trick dont know why your config files aren't writable :S

---


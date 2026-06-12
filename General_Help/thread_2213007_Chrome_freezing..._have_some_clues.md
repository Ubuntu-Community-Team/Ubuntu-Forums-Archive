---
title: "Chrome freezing... have some clues"
date: 2014-03-24
forum: General Help
---

### Post by mobrien1182 on 2014-03-24
Hello,

I was recently on Ubuntu 13.04 and using Google Chrome as my browser. My PC froze up one night (I pushed the PC mach against the wall. Maybe a PCI card came unseated or something).

When I booted back up, it did a fsck and found errors. Nothing major.

After that (maybe coincidentally?) Chrome would lock up after a few minutes of running (turns grey, no input response). Things I've tried (none have worked):
[LIST]
[*]Uninstall - re-install Chrome
[*]Move my profile folder to ".bak" (essentially creating a new profile)
[*]Upgraded to Ubuntu 13.10
[*]Complete uninstall chrome and re-install AND create new profile
[/LIST]

Some clues:
[LIST=1]
[*]While Chrome is running, "gnome-keyring-daemon" is using 100% of one CPU
[*]As soon as Chrome freezes, GKD goes back to 0-2%
[*]Everything in Chrome seems to be synced in my "new" profile except my stored passwords
[/LIST]

So, I wonder if this has something to do with the Gnome Keyring not being able to sync my passwords.

Has anyone seen this before? Any ideas?

Thanks,

--mobrien118

---

### Post by mobrien118 on 2014-04-04
OK, more clues!

It started working without freezing for about a week, then started locking up again...

Still doing the same thing where "gnome-keyring-daemon" is using high CPU and then, when it stops, Chrome stops...

---

### Post by mobrien118 on 2014-04-29
So, I ran it from the console and I'm getting this error message when it freezes:
> [20955:20955:0429/060724:ERROR:model_association_manager.cc(420)] Passwords datatype error was encountered: Association timed out.
[20955:20955:0429/060724:ERROR:model_association_manager.cc(289)] Failed to associate models for Passwords
[20955:20955:0429/060724:ERROR:model_association_manager.cc(420)] Autofill Profiles datatype error was encountered: Association timed out.
[20955:20955:0429/060724:ERROR:model_association_manager.cc(289)] Failed to associate models for Autofill Profiles
[20955:20955:0429/060724:ERROR:model_association_manager.cc(420)] Autofill datatype error was encountered: Association timed out.
[20955:20955:0429/060724:ERROR:model_association_manager.cc(289)] Failed to associate models for Autofill


Anyone?

---

### Post by jim.tykal on 2014-05-12
Same problem here - same error messages when launching from console. Just started a couple days ago after latest ubuntu 12.04 package manager updates.

---

### Post by mobrien118 on 2014-05-12
Yeah, so, for me it stopped for maybe 2 weeks then started again.

I *DO* have some new information, though:
Sometime after you launch Chrome (but before it crashes, obviously) go kill gnome-keyring-daemon. That will keep Chrome from locking up, but other programs will re-start the daemon as needed, so it is not too big of a deal.

Obviously, this is not the "right" way (e.g. ymmv, it may break other stuff, you may lose all of your passwords) and is more of an informational/troubleshooting step.

At least I'm glad to know I'm not the only one.

Another note: I have thousands of passwords stored in Chrome, so that may contribute to it. Do you?

Thanks,

--mobrien118

---


---
title: "Going back to 18.04 from 20.04"
date: 2021-07-05
forum: General Help
---

### Post by Curt Carpenter on 2021-07-05
Has anyone here reverted to 18.04 from 20.04 due to difficulties with the 20.04 GUI (eg. scroll bars too small for comfort)?  If so -- any advice on how to go about going back short of starting over with a bare hard drive?

---

### Post by ActionParsnip on 2021-07-05
You will need to reinstall. Wipe the current install from the system and reinstall with the release you desire. You will need to restore your user data from your backups

---

### Post by QIII on 2021-07-05
Might it not be a better use of your time to ask the community how to address each particular difficulty you are encountering?

By going back to 18.04, you are going back to an older kernel and shaving two years off of your support period.  If you are running a flavor, you are effectively taking yourself back to an unsupported version.

---

### Post by guiverc on 2021-07-05
I regularly QA-test and use *upgrades via re-install*.  When I use it for my real installs; it's nearly always forward (ie. to later release) though I have used it to go backwards many times before.

In QA-testing; I don't generally consider what release was there before hand, as current focus is on *focal* (*ie. what will be 20.04.3 in a little under six weeks*) and *impish* (*what will be 21.10 in October*) those are my current switches (forward & back).

As an *upgrade via re-install* erases system directories; the prior release does **not** matter; though there can be consequences with application data.
[B]
Example of problems (long ago).[/B]

I loved GNOME2; so loved Ubuntu 11.04 using the *Classic* mode, but it was different in 11.10 & later so I (*eventually)* reverted back.. Somewhere around that time `evolution` (my chosen  MUA or mail client) added newer features which I thought was great & thus started using them.  On reverting back to a prior release; all emails where I'd used those 'newer' features weren't there.. The database of my mail had been altered in a way the older program couldn't handle, so it just ignored those emails...

Took me awhile to find that issue (*I was scared loads of my email was being deleted; nope, if it'd been tagged, color coded using the newer features in the later version; the older evolution software was unable to handle it & just ignored those emails*).   When I eventually *release-upgraded* again to a release that contained a later version of `evolution` my email returned.

I've also had issues with `liferea` (RSS) where different versions used different databases, and the older version cannot handle the *upgraded* database. The later version can usually cope with earlier versions, but the older version can't know about newer versions (*programmers don't have time machines or blue police-tardis boxes*).

*Note:  I'm using `liferea` and `evolution` as examples only...  *

ie. Yep it's possible & rarely has issues.

Issues can occur - you need to check for every application you rely on and store data in; as to what changes occurred between those versions of programs.

An *upgrade via reinstall* which is a *Something-else/Manual Partitioning *where you select your existing partitions, and do **not**format any partition will cause

- your existing packages to be noted
- system directories are erased
- new system installed
- additional packages you had installed will be added (if available for release being installed)
- no user data is touched (unless you format!)
- user is asked to reboot.

Note: Errors on some packages not being able to restored is common & actually normal (when changing release). I'd suggest not filing a bug, just peruse the list & correct yourself. Most errors are from 3rd party sources - thus not Ubuntu packages anyway; or relate to things like python2, Qt4 reaches EOL & thus removal in 2019 for example.

Also note:  As system directories are erased; this is not a problem for desktop apps, but server apps often store config files within system directories, so restoration of data is required if using server applications.

---

### Post by kingpenguin on 2021-07-08
As everyone as stated so far the only way to go back would be to reinstall. I would recommend you to start looking into a program called timeshift which will allow you to back up everything outside of the home directory and allow you to restore your system from snap shots with a few clicks. It is a really awesome piece of software that will make your life easier next time.

---

### Post by monkeybrain20122 on 2021-07-09
Seems that with things like scrollbars you can probably fix it with a gnome extension or editing some css files. I don't use gnome shell but I remember I was able to adjust things like the width of the top bars with csss hacks.


I second QIII, better ask a question about your specific difficulties, the solution may turn out to be a lot easier and much less drastic than reinstalling the OS.

---

### Post by Curt Carpenter on 2021-07-18
> **Curt Carpenter said:**
> Has anyone here reverted to 18.04 from 20.04 due to difficulties with the 20.04 GUI (eg. scroll bars too small for comfort)?  If so -- any advice on how to go about going back short of starting over with a bare hard drive?

Thanks to everyone for the inputs.  I ended up just starting over with a clean drive and a new 18.04 ISO,

---


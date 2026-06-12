---
title: "No updates since Dec 17th - what's going on?"
date: 2021-01-01
forum: General Help
---

### Post by GhX6GZMB on 2021-01-01
Perhaps Ubuntu is now 100% perfect, but it's a bit hard to believe.

Since Dec 16th/17th, sudo apt update keeps reporting that "All packages are up to date."

I find it a bit hard to believe, but even changing mirrors brings no change.

Does anyone know what's up here?

---

### Post by TheFu on 2021-01-01
php, libvirt, apertium were updated here last Saturday. These aren't typical "desktop" packages.
It is natural for updates to be less in Dec/Jan as part of the holiday cycle.

---

### Post by QIII on 2021-01-01
Show me a "100% perfect" OS and I'll show you an OS with serious security flaws.

I vote to holiday season, too.

---

### Post by guiverc on 2021-01-01
It'll depend on what you have installed (not just your Lubuntu 20.04 LTS base, but your additional packages added) whether or not you have updates.

The latest release usually has the most updates (that&#8217;s *groovy*/20.10, of course ignoring development/*hirsute*). Older *stable* releases get fewer generally (only back-ported security updates)

I work with the Ubuntu Weekly Newsletter, [the last UWN issue #623]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue663") has a very clear

> Security Updates

No activity this period.

A single `mutter` update was listed for that week for `focal`/20.04, but if you don't have `mutter` installed you won't have had that.

There were more the week before [UWN #622]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue662"), but you can check yourself (it's a weekly publication).

[https://ubuntuforums.org/forumdisplay.php?f=243](https://ubuntuforums.org/forumdisplay.php?f=243)

and it's found right here on the Ubuntu Forums :)

---

### Post by wildmanne39 on 2021-01-01
> **guiverc said:**
> It'll depend on what you have installed (not just your Lubuntu 20.04 LTS base, but your additional packages added) whether or not you have updates.

The latest release usually has the most updates (that&#8217;s *groovy*/20.10, of course ignoring development/*hirsute*). Older *stable* releases get fewer generally (only back-ported security updates)

I work with the Ubuntu Weekly Newsletter, [the last UWN issue #623]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue663") has a very clear



A single `mutter` update was listed for that week for `focal`/20.04, but if you don't have `mutter` installed you won't have had that.

There were more the week before [UWN #622]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue662"), but you can check yourself (it's a weekly publication).

[https://ubuntuforums.org/forumdisplay.php?f=243](https://ubuntuforums.org/forumdisplay.php?f=243)

and it's found right here on the Ubuntu Forums :)

+1 to this ^^^

---

### Post by ActionParsnip on 2021-01-01
Christmas change freezes in IT are common. Are you not familiar with this?

---

### Post by grahammechanical on 2021-01-01
Even the 21.04 development version has had very few updates during this time of the year. Governments require employers to give paid leave and that would apply to paid developers. I imagine that community developers also like some time off during the year, as well.

Regards

---

### Post by walts48 on 2021-01-02
The excuse for Thunderbird not being updated since:

> thunderbird (1:68.10.0+build1-0ubuntu0.18.04.1) bionic; urgency=medium

  * New upstream stable release (68.10.0build1)

Wed, 01 Jul 2020 16:03:29 +0200

is what?

The current release is 78.6.0, released on December 15, 2020

Version 68.12.0 was released on August 25, 2020.

---

### Post by Dennis N on 2021-01-02
> **walts48 said:**
> The current release is 78.6.0, released on December 15, 2020. Version 68.12.0 was released on August 25, 2020.
If you must have the latest, you can install the Flatpak for Thunderbird:
```
dmn@Tyana-vm:~$ flatpak search thunderbird
Name                   Description                                                                           Application ID                       Version      Branch      Remotes
Thunderbird            Email, RSS and newsgroup client with integrated spam filter                           org.mozilla.Thunderbird              78.6.0       stable      flathub

```

---

### Post by ajgreeny on 2021-01-02
> **walts48 said:**
> The excuse for Thunderbird not being updated since:



is what?

The current release is 78.6.0, released on December 15, 2020

Version 68.12.0 was released on August 25, 2020.
Please do not start this specific discussion once again about the thunderbird version in Ubuntu which you spoke of at great length in the thread at [https://ubuntuforums.org/showthread.php?t=2455211](https://ubuntuforums.org/showthread.php?t=2455211)

It is unnecessary, and it adds nothing to the discussion of package upgrades in general that this thread is intended to ask about.
You should also be aware that this forum has no way to influence the decisions that Canonical makes about such things as the package versions in the Ubuntu supported versions.

---

### Post by howefield on 2021-01-03
> **ml9104 said:**
> Since Dec 16th/17th, sudo apt update keeps reporting that "All packages are up to date."

You could subscribe to the relevant mailing list, or simply just browse and read it online.

For 20.04, [https://lists.ubuntu.com/archives/focal-changes/](https://lists.ubuntu.com/archives/focal-changes/)

---


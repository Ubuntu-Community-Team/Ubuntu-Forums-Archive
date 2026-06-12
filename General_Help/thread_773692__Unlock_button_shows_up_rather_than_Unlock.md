---
title: "_Unlock button shows up rather than Unlock"
date: 2008-04-29
forum: General Help
---

### Post by ADINSX on 2008-04-29
I hope this hasn't been asked/answered before (I did look as thoroughly as I could), but this has only recently become a problem (didn't start until today). When I have an implicit authorization set to "Admin authorization (one shot)" on active console, and I try to use an unlock button (anywhere, be it network config or time and date), I see a *truly* grayed out button (clicking does nothing), and it is shown as "_Unlock" rather that "Unlock". I looked in the bugs.launchpad.net bug tracker, and was unable to find any problems that match mine. The oddest part is that everything was working fine the other day, with the same policy kit configuration.

When I change the authentication to "admin authentication" (minus the one shot), it works correctly. Also, if I set "console = Admin authentication (one shot)", it also works correctly when I am logged in as a non-privileged user.

The only things I have changed recently are my gnome theme, and my sudoers file. However, changing my theme and sudoers file back to their previous settings does nothing to help, so I have a feeling they are not related to my problem.

Is this a "feature" that I am completely missing the point of?

Screenshot:

[IMG]http://img80.imageshack.us/img80/9137/screenshot1ym8.png[/IMG]

---

### Post by gozotto on 2008-04-30
Are you connected locally or via NX?
If you are login remotely via Nx from NoMachine or freenx there exists a problem with the policykit.
See thread:
[http://ubuntuforums.org/showthread.php?t=712006]("http://ubuntuforums.org/showthread.php?t=712006")

---

### Post by ADINSX on 2008-05-03
> **gozotto said:**
> Are you connected locally or via NX?
If you are login remotely via Nx from NoMachine or freenx there exists a problem with the policykit.
See thread:
[http://ubuntuforums.org/showthread.php?t=712006]("http://ubuntuforums.org/showthread.php?t=712006")

I'm not logging in remotely, I'm logging in locally.

My problem isn't that I can't use policykit *period*, because I can use it under most conditions (I just make sure nothing is set to admin auth one shot). So this isn't a *critical* issue for me, but it does serve as an annoyance, because I would like to use the one shot setting.

---


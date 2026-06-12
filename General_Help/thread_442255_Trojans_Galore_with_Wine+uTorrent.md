---
title: "Trojans Galore with Wine+uTorrent"
date: 2007-05-13
forum: General Help
---

### Post by SatNav on 2007-05-13
I've got a problem which, while not exactly catastrophic, is **exceptionally** annoying.

Since the Feisty upgrade I've been running without a firewall - stupid, I know. Anyways, I've been running utorrent with wine, and it's all been fine and dandy, until I finally got around to installing firestarter and set the outgoing policy to restrictive mode. Suddenly I was seeing hundreds of blocked outgoing connections, belonging to services with such terrifying names as 'Back orifice', 'Cheeseworm', etc.

I think I'm right in believing that these worms/trojans/whatever are pretty harmless, since they're running in wine, and can only affect windows executables (please correct me if I'm wrong). But they were pretty annoying - firestarter was in a constant warning state, and they must have been using up a few CPU clicks, at the speed they were going.

So I completely removed wine, utorrent, and any related exe's and settings files I could find, before reinstalling a newer version of wine, and a fresh version of utorrent from the official site. Everything seemed fine, no unexpected connections appeared, so I set up utorrent's settings, but DIDN'T load any torrents.

Five minutes later, completely out of the blue, a huge rush of the unwanted connections started up again. I can stop them by closing utorrent, but as soon as I open it, they start up again.:mad: 

Does anyone have any idea WTF is going on - I can't find anything relating to this either from google, or on these forums, and would appreciate any help.

Cheers,
Mark

---

### Post by raffytaffy on 2007-05-13
is there a specific reason youre running a torrent client on WINE? why not just get azureus or one of the other linux ones. As to the connection problem, i have no clue. i would never run torrent with wine.

---

### Post by SatNav on 2007-05-13
Personal preference. And familiarity - I'm a fairly recent linux convert (last november), and was using utorrent previously.

Before the feisty upgrade, some odd combination of wine and my gfx card/drivers made utorrent so unstable it would periodically crash so hard I couldn't even kill X, and would have to hard reboot. So I used Azureus for about 6 months, and while it was ok, I found it generally more cumbersome to use - clunky, bloated, and while it had a lot of features, it was missing a couple I really wanted.

Basically I jumped at the chance to start using utorrent again. (edit: although I do have an eye on deluge - that looks like a real competitor)

Anyways, if one win32 app can get hit this hard, whats to stop anything else I want to run in wine getting infected as well? And I KNOW utorrent can't just download a virus, and infect itself at whim, so it's got to come from somewhere.

So please, anyone?

---

### Post by SatNav on 2007-05-13
aha. Im may just be the worlds biggest r-tard.

the second time the connections all started up, it was because of my RSS torrents. my firewall is only set to allow outgoing bittorrent connections between ports 6881-6889, so when my rss's started up, it wanted to send to all sorts of weird and wonderful port numbers - I just assumed it was trojans again.

well... I havent been to bed in over 24 hours - Im very tired - thats my excuse

---

### Post by zvacet on 2007-05-13
You don´t need Firestarter at all.Download Avast for linux and scen just wine folder.I mean you can scen all filesystem but I don´t think you will find anything there.In short try Avast and see if it mach your needs.

---

### Post by orb9220 on 2007-05-13
I find kTorrent great even tho it is an KDE app. But in gnome I have found many apps lacking in power and have to use a KDE app.

Deluge wasn't even close to getting me a decent download rate compared to kTorrent. Wish the best for gnome apps. But alot of them have a ways to go to catch up.

And No I do love Gnome over KDE and hope that gnome will catch up with matured apps for gnome.

---

### Post by chochem on 2008-05-28
Though not exactly awash with such services, I've seen this too. Starting utorrent while watching firestarter's active connections has on a couple of occasions reported the services 'GateCrasher' and/or 'Backdoor Orifice 2k' (by program 'wineserver'). 

Does firestarter itself determine the nature of the service? And is this reliable in the case of a wine program? Also, if it's true, what is the likely spread of contamination? the utorrent binary? or some wine stuff?

EDIT: tried deleting utorrent.exe and replacing  it with a version fresh from utorrent.com chown'ed to root and set to read-only permission for all users. Backdoor Orifice still pops up...

EDIT: Another thought... I tried using the new utorrent.exe without my utorrent profile and loaded a single torrent... and nothing. So I figure, maybe it's the torrents? More specifically some user on that torrent, that is infected? The Backdoor connection is always to the same IP and while firestarter lists it as originating from me, it does that for all connections (since as far as I've understood, only ingoing connections initiated by me are allowed?)

---

### Post by Fatman_UK on 2008-05-28
> **SatNav said:**
> And I KNOW utorrent can't just download a virus, and infect itself at whim, so it's got to come from somewhere.

Perhaps uTorrent.exe was infected to begin with? Just an idea... maybe you copied it over from a Windows box not realising it was infected.

> **SatNav said:**
> I think I'm right in believing that these worms/trojans/whatever are pretty harmless, since they're running in wine, and can only affect windows executables (please correct me if I'm wrong)

I'm no expert, but I would delete my Wine profile and start over, just in case. Paranoia never hurt anyone ;) . If these worm/Trojan things are running and able to make connections I see no reason why they can't, for instance, read your /etc/passwd or find a credit card number on your system [once the bot-master realises you're running Wine not Windows, of course].

---


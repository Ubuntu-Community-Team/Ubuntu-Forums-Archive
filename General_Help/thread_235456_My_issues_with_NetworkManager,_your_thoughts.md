---
title: "My issues with NetworkManager, your thoughts?"
date: 2006-08-13
forum: General Help
---

### Post by matthias_k on 2006-08-13
Hi,

at first I was pleased with the idea that there is finally a software which supposedly allows you to roam between WLANs seamlessly. But actually I'm rather annoyed with NetworkManager.

1) Each time I want to connect to an encrypted wireless network, NM looks up the passphrase in something called the "keyring". For this to work, I have to supply a password. I have to supply a password to supply a password? Yeah. This is simply annoying, I didn't need this when using wpa_supplicant only.

2) After booting Ubuntu, every first attempt by NM to connect to my wireless network FAILS. I have to wait like a minute or so until it stops retrying, then explicitly select the connection and then it works. I mean, huh?

3) I find it highly annoying that NM doesn't connect until after the applet is loaded, which is after the desktop (GNOME) has fully loaded. This renders other applets which connect to the internet useless, because there simply is no connection until the desktop has completely loaded. This wasn't the case with wpa_supplicant either.

4) It's SLOW. It takes at least 30 seconds to connect to a WLAN, how come?+

I don't know, I'd really want to use this app for convenience, mabye I'm just missing something, but right now it rather seems less convenient than my good ol' "switch-network" script which copies around interface setups...

Any hints/thoughts?

---

### Post by orb9220 on 2006-08-14
Well your right and this issue work around is discussed in the wireless section. Something about recompiling the latest and setting keyring to same password as your system.

Sorry about the startup issue's but I see no way around that have same problem with gmail notify falling to connect and weather.

Another annoying but not totally nm's I think is if I boot into xubuntu using the xfce4 desktop then 3 yes THREE instances startup in tray and I have to close two of them manually.

The other pet peave is the so called up to date is 0.6.2 but if you go to their site [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) you will see that their site has 0.6.3 back in june and 0.6.4 in july so why or how many month's does it take?

They don't even give a link for feedback or questions. Which tells me they have no intention of giving info to mere mortals.

---


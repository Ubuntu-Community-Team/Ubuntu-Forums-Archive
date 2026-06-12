---
title: "Why is tor browser not included in Ubuntu repository?"
date: 2023-01-23
forum: General Help
---

### Post by Scottie303 on 2023-01-23
Why is tor browser not included in Ubuntu repository for easy installation?

I had to go to [https://www.torproject.org](https://www.torproject.org) in order to install it.

That must mean that Ubuntu is compromised by the security services: CIA Mi6 FBI

Ubuntu is no safer than Windows, then, right?

---

### Post by Holger_Gehrke on 2023-01-23
Actually, tor is in the repositories (not the tor-browser-bundle, just tor - the onion router - itself) but it has a history of slow updates; not really surprising, Ubuntu has a hard enough time keeping up with less niche packages and for stability reasons packages are held at the version they had at release of a version of Ubuntu with only bugfixes getting ported back from the newer versions. For that reason the tor project tells you not to use tor from Ubuntu.

There actually is a package torbrowser-launcher - mainly a python script - which simplifies the process of downloading and installing the tor browser bundle from the tor project.

Holger

---

### Post by guiverc on 2023-01-23
I've always used `torbrowser-launcher` on new installs (from Ubuntu repositories)

[https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=torbrowser&searchon=names](https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=torbrowser&searchon=names)

though as it's community supported; you'll need to *enable* universe if using Ubuntu Desktop/Server & not a *flavor* (which have 'universe' enabled by default).  This is the method [[COLOR=#000000]Holger_Gehrke[/COLOR]]("https://ubuntuforums.org/member.php?u=1961578")[COLOR=#000000] mentions (*as a script*), but being in the repositories as a package I find it easy.[/COLOR]

There are odd occasions where the package fails to install (Upstream Tor have made a change to something), but if you file a bug report on it, the *maintainer* usually fixes it within a few days (*or slightly longer due to illness/covid etc*) once bug has been filed.

---

### Post by Scottie303 on 2023-01-24
Thanks guys, The way governments are going we will need more anonymity online in the future.

---

### Post by ActionParsnip on 2023-01-24
Please mark as solved if this is now OK

---


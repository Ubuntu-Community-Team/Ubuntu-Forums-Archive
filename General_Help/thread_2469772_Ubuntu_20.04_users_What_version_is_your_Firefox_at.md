---
title: "Ubuntu 20.04 users: What version is your Firefox at?"
date: 2021-12-08
forum: General Help
---

### Post by ardouronerous on 2021-12-08
I'm running Xubuntu 20.04 and for some reason, there's a delay in Ubuntu's Firefox updates. As far as I know, Firefox has released 94.0.2 and now has released Firefox 95.0.

But Ubuntu's Firefox version remains at 94.0. Is there a reason for this delay? Is anyone else experiencing this or is there something wrong with my update server? Please confirm, thanks.

---

### Post by T6&amp;sfpER35% on 2021-12-09
i don't use firefox ,but it's installed . Mine's also still 94.0 , with no option to update .

---

### Post by ardouronerous on 2021-12-09
> **3nd said:**
> i don't use firefox ,but it's installed . Mine's also still 94.0 , with no option to update .

Well, at least I'm not the only one experiencing this, so thanks for the confirmation.

---

### Post by CatKiller on 2021-12-09
New versions of browsers need to be tested and built for all the supported Ubuntu releases (there are a lot) through the [Stable Release Updates](https://wiki.ubuntu.com/StableReleaseUpdates) process. Normally packages get bug and security fixes backported, but not new features, but things like browsers mix all those things together. Since that takes a while, Chromium (the non-default browser) is distributed as a snap now, so that the build only needs to be done once and will work on every release (and will work on other distros, too). Mozilla have asked that Firefox should only be done as a snap, too, for the same reason, and that will be the default at some point in the future.

---

### Post by ajgreeny on 2021-12-09
> **CatKiller said:**
> New versions of browsers need to be tested and built for all the supported Ubuntu releases (there are a lot) through the [Stable Release Updates](https://wiki.ubuntu.com/StableReleaseUpdates) process. Normally packages get bug and security fixes backported, but not new features, but things like browsers mix all those things together. Since that takes a while, Chromium (the non-default browser) is distributed as a snap now, so that the build only needs to be done once and will work on every release (and will work on other distros, too).[COLOR="#0000FF"] Mozilla have asked that Firefox should only be done as a snap, too, for the same reason, and that will be the default at some point in the future.[/COLOR]

But I believe they will still make the .tar.gz available, so if you do not want any snaps in your system you can run FF direct from the executable file in the archive without even installing it.

Or have I got that wrong?

That is how I run the most recent version of FF in Debian which otherwise uses the ESR version only.

---

### Post by Dennis N on 2021-12-09
I use the Flatpak Firefox - it's version 95.0 (as of Dec 9)

---

### Post by CatKiller on 2021-12-09
> **ajgreeny said:**
> But I believe they will still make the .tar.gz available, so if you do not want any snaps in your system you can run FF direct from the executable file in the archive without even installing it.
The announcement about it is [here.](https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210) 
> **After the transition, do I HAVE to use the snap?** We (Mozilla and the Desktop Team) recommend the snap, but, if you’d prefer otherwise, Mozilla still offers their distro-agnostic builds for amd64 and i386.
It's about not having the update delay for normal users. Those who want to run things manually or use a PPA will still be able to, just like they can with chromium.

---

### Post by grahammechanical on 2021-12-09
I am using Ubuntu 20.04 and I have Firefox 95 installed. Yes, it is the snap version. It is customary for there to be a delay in upgrading applications like Firefox on LTS versions. The reasons given in an earlier post are sufficient to me. Usually it is the 6 monthly released standard versions of Ubuntu that get the new versions of Firefox first. That will change.

Ubuntu 20.04 users who upgrade to 22.04 will experience the deb version being removed and the snap version being installed. This happened to me with an install of 21.04 when I upgraded it to 21.10. So, I got in first. I removed the deb version of Firefox and installed the snap version.

Consider the recent situation with Thunderbird which is not available as a snap. To fix a security flaw Thunderbird 91 had to be back-ported to 18.04 and 20.04 to replace Thunderbird 78. A snap version of Thunderbird would have made the upgrade automatic.

[https://www.omgubuntu.co.uk/2021/11/thunderbird-91-backport-ubuntu-18-04-20-04-lts](https://www.omgubuntu.co.uk/2021/11/thunderbird-91-backport-ubuntu-18-04-20-04-lts)

Regards

---

### Post by T6&amp;sfpER35% on 2021-12-10
well what do you know , just this morning got an update message for FF 95.0...
so there ya go ardouronerous ,calm down your's will arrive soon lol
ps. i use the main ubuntu mirror for updates

---

### Post by kurt18947 on 2021-12-10
> **grahammechanical said:**
> I am using Ubuntu 20.04 and I have Firefox 95 installed. Yes, it is the snap version. It is customary for there to be a delay in upgrading applications like Firefox on LTS versions. The reasons given in an earlier post are sufficient to me. Usually it is the 6 monthly released standard versions of Ubuntu that get the new versions of Firefox first. That will change.

Ubuntu 20.04 users who upgrade to 22.04 will experience the deb version being removed and the snap version being installed. This happened to me with an install of 21.04 when I upgraded it to 21.10. So, I got in first. I removed the deb version of Firefox and installed the snap version.

Consider the recent situation with Thunderbird which is not available as a snap. To fix a security flaw Thunderbird 91 had to be back-ported to 18.04 and 20.04 to replace Thunderbird 78. A snap version of Thunderbird would have made the upgrade automatic.

[https://www.omgubuntu.co.uk/2021/11/thunderbird-91-backport-ubuntu-18-04-20-04-lts](https://www.omgubuntu.co.uk/2021/11/thunderbird-91-backport-ubuntu-18-04-20-04-lts)

Regards

I uninstalled Thunderbird 78 and installed the Thunderbird 91 snap. I don't know that there's a Thunderbird 78 snap.

---

### Post by ActionParsnip on 2021-12-10
[https://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=focal&section=all](https://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=focal&section=all)

This link will always show you what version Firefox is at. You can search the official repositories as you need

---


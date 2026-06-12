---
title: "How to ask updating packages in universe repository?"
date: 2021-04-19
forum: General Help
---

### Post by inurindd on 2021-04-19
Hello.

I'm starting using ubuntu 20.04 and find a open-source package which I want to use is old version release in universe repository.
How to ask ubuntu developers or maintainers to replace from old to the newest?

Thanks,
inurindd

---

### Post by scorp123 on 2021-04-19
> **inurindd said:**
>  I'm starting using ubuntu 20.04 and find a open-source package which I want to use is old version release in universe repository. 
Old versions are more stable, better tested. That's the very reason why a long-term distribution such as Ubuntu 20.04 with 5 years of support is using those.

> **inurindd said:**
>  How to ask ubuntu developers or maintainers to replace from old to the newest?
They can't do that even if they wanted to, as per policy of providing a stable, well-tested long-term distribution which is exactly the point of Ubuntu 20.04.

Alternative idea:

Why not use alternative package sources such as e.g. FlatPak? The chance of your application existing in a higher version there is much better.
[https://linuxhint.com/install-use-flatpak-ubuntu/]("https://linuxhint.com/install-use-flatpak-ubuntu/")

Also, there are so called "PPA" that sometimes may contain newer versions of certain packages than what is inside the standard repositories. But PPA packages might break stuff. Since you didn't tell us which package it is you want I can't point you to any PPA archive. You'll have to google that yourself then.

Which application is it anyway?

---

### Post by inurindd on 2021-04-19
Hi scorp123,
Thank you for your reply and I understand the policy:p

I've installed Kismet and it's "kismet-plugins_2016.07.R1-1.1~build2_amd64.deb" in universe repo. However, I'd like to use Kismet(2020-12-R3) for supporting 802.11ac and have rich web UI.

Thanks

---

### Post by CatKiller on 2021-04-19
> **inurindd said:**
> How to ask ubuntu developers or maintainers to replace from old to the newest?

You don't. The Universe repository is specifically those packages that aren't maintained by the Ubuntu developers. Even for the packages that *are* maintained by Ubuntu developers, with a small handful of specific exceptions, packages aren't upgraded to a higher version number during an Ubuntu release's lifetime; security and bug fixes are backported to the versions in the repositories.

If you just want a newer version to use you might be able to find a PPA, snap, Flatpak, or AppImage of the software in question. If you want Ubuntu to pick up newer versions of the software in future Ubuntu releases you can become its package maintainer for Ubuntu (or Debian, or both).

---

### Post by CatKiller on 2021-04-19
> **inurindd said:**
> I've installed Kismet
Kismet devs have made [their own repository](https://www.kismetwireless.net/docs/readme/packages/#ubuntu-2004-focal-intel).

---

### Post by ActionParsnip on 2021-04-19
Another option:
[https://launchpad.net/ubuntu/+ppas?name_filter=kismet](https://launchpad.net/ubuntu/+ppas?name_filter=kismet)

Could try one of those. These obviously come with the caveats of a PPA. Remeber to filter the PPA for your release. Not all PPAs support all releases

---

### Post by rsteinmetz70112 on 2021-04-19
I have an application which maintains it's own repository and I simply add that repository to my sources. Then whenever the developers push a new update I get it in the normal update process. As long as the developers keep it up to date it works well. I'm a little leery of PPAs since I don't know how well they will be maintained.

Another option is to use a snap, if one exists.

---

### Post by CatKiller on 2021-04-19
> **rsteinmetz70112 said:**
> I'm a little leery of PPAs since I don't know how well they will be maintained.
It's swings and roundabouts, really. PPAs are hosted on Launchpad, so there's an avenue to get it sorted if the packages turn out to be malicious, and ppa-purge is a really handy tool. But, yes, the packages could have been created by some random Internet person rather than the application's devs. Generally because the dev doesn't want to, though. 

Snaps are intended to address the discoverability issue that PPAs have, but they still suffer from the potential abandonment issue that PPAs and other external repositories have, and they could also come from a random Internet person rather than the application's devs; if a dev wants to officially take over maintenance of an existing snap, though, then they can.

---

### Post by ajgreeny on 2021-04-19
This forum is a great place to ask before enabling any PPA; it is very likely that many users on this forum have used the "good, safe" PPAs and also that users will already know of problems that might arise if a PPA is not safe.

For the record, I have many PPAs enabled, eg, openshot, handbrake, chromium-dev, audio-recorder and Libre-office, all of which are working without any difficulties or problems.

---

### Post by inurindd on 2021-04-20
Thanks all again:)

---


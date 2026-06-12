---
title: "Will there be a Ubuntu 23.10.1 for Raspberry Pi"
date: 2023-12-20
forum: General Help
---

### Post by fckwan on 2023-12-20
[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)
The Ubuntu download link for Raspberry Pi only offer version of Ubuntu 23.10

Will there be a Ubuntu 23.10.1 available?

Or is there a command that can update the current Ubuntu 23.10 to 23.10.1

I ran sudo apt update 
and sudo apt upgrade.

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 23.10
Release:    23.10
Codename:    mantic


But my Raspberry Pi 4B is still in Ubuntu 23.10 not 23.10.1

---

### Post by MAFoElffen on 2023-12-20
Only LTS releases get point releases. Interim releases do not, and their support lifecycle is only 9 months of support. The next LTS (Noble 24.04) releases in April.

---

### Post by TheFu on 2023-12-20
You'll want to learn about the different types of releases Canonical has.  LTS and non-LTS.

There is 1 LTS release every other year. **_Even years, in April_**.   Here's the pattern: 16.04, 18.04, 20.04, 22.04 ....... YY.MM   Can you guess the next one?

All other releases are non-LTS with only 9 months of support, but usually it is smart to either avoid these completely if you need production level code or if your hardware is extremely new, you may need to use a non-LTS, but expect to migrate to a new OS every 6 months until you can get back onto an LTS release.

Whenever an LTS is released, I like to wait a few months for any early huge bugs to be addressed after more than 5K users have tested.

Further, LTS releases have different support periods based on the flavor.
Standard support for most flavors is 3 yrs and there is NO ESM support at all. These are officially called "interim releases".
Standard support for Ubuntu Server and the flagship Ubuntu Desktop (running Gnome 4+) is 5 yrs.  ESM is available for both by signing up. That brings the support period to 10 yrs, but really having any GUI for that length of time becomes a problem as any internet-connected GUI tools will likely need updating for security protocol changes before 5 yrs.  This is very important for web browsers and email tools, but others are impacted as well.  For individuals, a few (3-5, I don't recall exactly) systems can get ESM support for free.  For Ubuntu Members, I think the number is like 50 systems.  Of course, anyone can pay for support too.   [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)  

Inside corporations, sometimes it isn't possible to migrate every 4-5 yrs for outside reasons, but the service has to be legally provided as long as possible.  At my $day_job, I used to scan computer junk dealers around the world for 25+ yr old components to keep a govt mandated service working.  When I go that added to my normal job, there were 150 systems using long outdated equipment.  We'd look everywhere for parts, sometimes stealing parts from our own equipment in service areas that had fewer clients to keep the service available in larger markets.  In the 8 yrs I had that project (in addition to my other concurrent 20 projects), the total number of working systems became less than 25.  Of course, we had alternative, supported, faster, cheaper, services for offer, but many of the smaller customers either couldn't afford to upgrade their side of the connection or the owners were ready to retire and nobody would buy their local, outdated, connections. Any change would put those small companies out of business.  In IT, change is constant.  Getting 20 yrs from equipment rarely happens, especially for connectivity.  In 2000, many people were still using dial up.  Imagine your equipment only supported 2400 baud connections and your business was built around that for the last 30 years.  Finding a working 2400 baud modem from 1-2 specific vendors would be nearly impossible. Now, consider that for enterprise equipment the market was never millions of modems, just 1000 world-wide. They stopped being made 20 yrs ago.  See the issue?

LTS releases are about stability for corporations and less about "new". That means that API changes shouldn't happen with just a few GUI program exceptions (web browsers and email programs). All others are likely to remain the same and can break.  The solution for those other programs to be updates are either PPA or snap or flatpak or AppImage versions of the software.

[https://ubuntu.com/blog/what-is-an-ubuntu-lts-release](https://ubuntu.com/blog/what-is-an-ubuntu-lts-release) has a chart/graph showing clearly the supported releases and the expected support periods.

---

### Post by fckwan on 2023-12-20
There is a Ubuntu 23.10.1 already released. But it is only for amd64 architecture and not arm (Raspberry Pi)

[https://releases.ubuntu.com/mantic/](https://releases.ubuntu.com/mantic/)

Because I saw the above website. That is why I ask will there be a Ubuntu 23.10.1 for arm architecture(Raspberry Pi).

---

### Post by ian-weisser on 2023-12-20
Reference: [https://ubuntuforums.org/showthread.php?t=2491556](https://ubuntuforums.org/showthread.php?t=2491556)
Reference: [https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-translation-incident-now-resolved/39365](https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-translation-incident-now-resolved/39365)

For those who missed it, some .iso images of 23.10 were indeed pulled, and replaced by 23.10**.1** to avoid confusion. This is a very rare event.

The Pi images were not among the affected builds. 23.10.1 will not be issued for Pi images. Go ahead and safely use the 23.10 Pi images.

---


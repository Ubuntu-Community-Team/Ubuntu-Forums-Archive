---
title: "software updates?"
date: 2007-10-09
forum: General Help
---

### Post by ZeldaFan on 2007-10-09
How do I get software updates for programs that I installed through downloading the respective tar.gz file from the website and such. For example, I installed openoffice through downloading the latest version from its website, how would I update that to its latest version. It doesn't show up to upgrade to 2.3 ( I have version 2.2) with software update. Same thing with amarok, even though I already installed it through the repositories, it doesn't show up to upgrade through software update. Currently I have version 1.4.5 but I am pretty sure a later version is available. I dont know how to get software updates for any of these. And also for all other programs I install in this way (not through synaptic or apt-get) do I have to manually update/upgrade them?

---

### Post by rsambuca on 2007-10-09
If you have installed a package using either apt-get or Synaptic Package Manager, then the automatic update notifier will inform you of any security updates.  If you manually installed a package, then you are on your own, although some programs will inform you of updates.

As a rule, Ubuntu doesn't often upgrade to newer versions of software during the 6month release cycle.  You will have to wait until Gutsy is released in a week and a half to get newer versions by default.

---

### Post by ZeldaFan on 2007-10-09
That doesn't make much sense to me....because I get software updates for other programs I have all the time. However, are you referring to the default Ubuntu repositories? If so, then you are then probably right, because I think I only receive updates to programs I installed from repositories that I manually added to the sources.list file. Is there any way I can disable that feature however? If I could, should I enable that feature?

---

### Post by rsambuca on 2007-10-09
Yes, I was talking about the ubuntu repositories.  Outside sources can obviously do whatever they want as far as updates go.

You can disable the updates, but I personally wouldn't, as the majority of the Ubuntu ones are security patches.

---

### Post by ZeldaFan on 2007-10-09
No, I am saying can I change the feature so that I get updates to my software whenever available, not all at once during the release of a new distro upgrade

---

### Post by rsambuca on 2007-10-09
I think the default is to check daily, but to set yours to whatever you wish, go to "System -> Administration -> Software Sources".  Go to the "Updates" tab, and set the Automatic updates section.

You realize that the ubuntu updates are primarily security patches, right?    Ubuntu is on a strict 6 month release cycle, so if you can't wait the 6 months and want immediate upgrades to new versions of programs, you should try a Rolling Release linux distribution such as Foresight Linux, Debian Sid, Arch, or Gentoo.

---

### Post by ZeldaFan on 2007-10-09
So lemme get this straight, programs are updated along with new distro releases, not in between. Or is it just the nature of Ubuntu to update its programs when it releases a disto upgrade? Taking amarok for example, the latest version is 1.4.7, I have version 1.4.5, which I installed through the repositories. So, Ubuntu will not upgrade to that latest version of amarok until the release of Gutsy Gibbon?

---

### Post by rsambuca on 2007-10-09
I don't know how many times you want me to explain this, but here goes again.

Security updates are released whenever they are found and fixed.

Specific program upgrades to new versions generally only occur with the next Ubuntu release.

You are correct, amarok will not be version 1.4.7 until Gutsy is released next week.  Afterall, it is only a 6 month release cycle.

Like I said, if you want the newest versions of programs immediately, then Ubuntu is definitely not the best linux distro for you.  Check out the rolling-release distros I mentioned in my last post.

---

### Post by ZeldaFan on 2007-10-09
Thanks, I get it now, I just wanted to make sure that everything on my system was working fine.

---


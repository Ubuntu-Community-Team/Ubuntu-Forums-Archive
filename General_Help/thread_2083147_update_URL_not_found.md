---
title: "update URL not found"
date: 2012-11-11
forum: General Help
---

### Post by Synoc on 2012-11-11
as I still believe there is no substitute for Gnome two (tried failback and Mate, still not as good), I have elected to stay with maverick. As such I believe launchpad is no longer hosting update sources for 10.10. I get the error:

```

Failed to fetch http://ppa.launchpad.net//libreoffice/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net//libreoffice/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```
so either the url has changed, been corrupted on my end, is actually no longer valid or there is a DNS  issue. In any case, I need to fix this issue and get that yellow warning triangle off my screen. any ideas?

---

### Post by ajgreeny on 2012-11-11
As you are aware, 10.10 is no longer supported and the repos have therefore been moved to become EOL.  That means you are able to update 10.10 using the EOL repos until it is fully up to date, as it was at the end of its support life, but from that point you can go no further, short of a distro update to a more recent ubuntu version.  However from 10.10 you would have to move to 11.04, also now out of support, so a clean installation of an alternative is really on the cards for you.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

10.04 is still supported at the moment and has gnome 2, but in another 5 months that will lose support, and from that time there will be no more gnome 2 in ubuntu.

Like you, I find I can not manage unity and therefore I chose to stick with 10.04.  In April next year I will start using Xubuntu 12.04, which can be made to look like and act almost exactly as gnome 2 does.  I say "almost" as there are some differences, but in my opinion Xubuntu will be the nearest we have to what I like to call a proper, menu driven desktop, like gnome 2.

---

### Post by Synoc on 2012-11-11
that was rather my fear. I may have to stick with the failback mode. Having tried Xfce I was not not impressed. given a few more years it may be up to snuff, but as of now, I gnome 3 failback seems to be what I will be forced to go with. I will look into it on a lab PC first.

for the immediate future, I have removed the offending PPAs from the update manager.

---


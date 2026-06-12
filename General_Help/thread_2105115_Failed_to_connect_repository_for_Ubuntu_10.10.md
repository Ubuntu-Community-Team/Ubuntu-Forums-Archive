---
title: "Failed to connect repository for Ubuntu 10.10"
date: 2013-01-15
forum: General Help
---

### Post by paldebojyoti on 2013-01-15
Hello,
I have been using Ubuntu 10.10 for last 1 and half years, but recently I am facing issue of connecting the repository and installing packages through synaptic package manager.
It would be very helpful, if anyone can tell me what is the issue? Are all the repositories for Ubuntu 10.10 not OK?

Please note that my Internet connection is fine.
Regards,
Deb

---

### Post by mikewhatever on 2013-01-15
The 10.10 repositories are gone (yes, all of them), as it has reached End of Life in April 2012.

---

### Post by Warren Hill on 2013-01-15
You will need to upgrade.  I depending on your PC you may wish to consider Xubuntu or Ubuntu 12.04.

I would stick to the LTS releases since as you are currently using 10.10 you are obviously not bothered by the latest features and LTS releases require you to update less often.

---

### Post by DaveB on 2013-01-17
Ummm, 10.10 repository is still around per this page:

[http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

Quote: "If you want to continue using an outdated release then edit /etc/apt/sources.list and change archive.ubuntu.com to old-releases.ubuntu.com".  That page has a useful sed script that worked for me.

---

### Post by snowpine on 2013-01-17
^---- **For educational/historical purposes only!** (like you are writing a research paper on obsolete Linux releases.) 10.10 repositories have received no security updates or bug fixes since April 2012 (nor will they ever); 10.10 is not recommended for everyday use for this reason.

---


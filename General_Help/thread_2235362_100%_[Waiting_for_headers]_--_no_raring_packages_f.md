---
title: "100% [Waiting for headers] -- no raring packages found"
date: 2014-07-20
forum: General Help
---

### Post by Sam_Zhang on 2014-07-20
I'm having an issue all of a sudden with running apt-get update. It gets stuck on 100% [Waiting for headers] after getting a 404 response from a few Ubuntu raring packages. My /etc/apt/sources.list is really sparse, with no references to raring anywhere. My sources.list.d/ directory contains more lines though:

adamzammit-pspp-raring.list      mercurial-ppa-releases-raring.list
audacity-team-daily-raring.list  mongodb.list
ehoover-compholio-raring.list    official-package-repositories.list
gandalf-pspp-raring.list         official-package-repositories.list.save
google-chrome.list               steam.list
google-earth.list                stebbins-handbrake-releases-raring.list
google-talkplugin.list           thomas_tsai-ubuntu-tuxboot-raring.list
heroku.list                      ubuntugis-ppa-raring.list
local-repository.list            ubuntugis-ubuntugis-unstable-raring.list
local-repository.list.save       webupd8team-java-raring.list
marutter-rdev-raring.list

Do any of these look like they might cause a problem?

Thanks

---

### Post by bapoumba on 2014-07-20
Raring has reached EOL last january and the repos are not on archive.ubuntu.com. Best to do is fresh install a supported release (14.04 Trusty is LTS) after backing up all your data. Saucy 13.10 has reached EOL on July 17th.

---

### Post by Impavidus on 2014-07-21
If you have no references to raring (13.04, end-of-live January 2014) in your sources.list, but have some in sources.list.d, this suggests that you're running a more recent Ubuntu release combined with PPAs for 13.04. It seems those PPAs have been taken off-line. Disable them and find alternatives.

If you're not running 14.04 now, either upgrade or do a fresh install.

---


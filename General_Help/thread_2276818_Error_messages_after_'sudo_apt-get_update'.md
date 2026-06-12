---
title: "Error messages after 'sudo apt-get update'"
date: 2015-05-05
forum: General Help
---

### Post by RayArdia on 2015-05-05
Using Ubuntu 14.04 
Have had some problems of late, difficulties in burning DVDs and more general system unpredictabilities. As a result of trying to use Kb3 to attempt a successful DVD burn (and failing) I needed to upgrade some packages (apt-utils,libapt.inst1.5, libapt-pkg4.12). After the attempted upgrade I was prompted either to update or to "maybe use --fix-missing"; as I'd no idea how to apply '--fix-missing' I just did another update.
This produced the following error messages:-

W: Failed to fetch [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. (Note: This seems to recur often these days after an update; I find its vagueness slightly ominous!)

I tried Launchpad, to get the ppa referred to above (W) but it wasn't there at all. What should I do please?

---

### Post by plucky on 2015-05-05
> **RayArdia said:**
> Using Ubuntu 14.04 
Have had some problems of late, difficulties in burning DVDs and more general system unpredictabilities. As a result of trying to use Kb3 to attempt a successful DVD burn (and failing) I needed to upgrade some packages (apt-utils,libapt.inst1.5, libapt-pkg4.12). After the attempted upgrade I was prompted either to update or to "maybe use --fix-missing"; as I'd no idea how to apply '--fix-missing' I just did another update.
This produced the following error messages:-

W: Failed to fetch [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. (Note: This seems to recur often these days after an update; I find its vagueness slightly ominous!)

I tried Launchpad, to get the ppa referred to above (W) but it wasn't there at all. What should I do please?

That [PPA](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/) does not have a repository for Trusty.

Open Software Sources and delete it from the list of Sources.

Then run ```
sudo apt-get update
``` and see if it now updates without any warnings

Good Luck

---


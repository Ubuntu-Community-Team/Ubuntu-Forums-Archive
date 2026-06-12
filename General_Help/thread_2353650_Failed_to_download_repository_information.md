---
title: "Failed to download repository information"
date: 2017-02-23
forum: General Help
---

### Post by Robbyx on 2017-02-23
I get the following when I try to update my software in 14.04 at first I get "failed to download repository information"

eventually I get:

W:Failed to fetch [http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I thought the way around the problem would be to upgrade to 16.04LTS by taking advantage of the software updater option but that fails because it could not detremine the upgrade

[I]An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu
[/I]

Is it to do with my running Gnome?

Any ideas please as to how to ensure that the correct repositories are accessed and I can upgrade my os?

Robin

---

### Post by Bashing-om on 2017-02-23
Robbyx; Yep;

 "404 Not Found" the system is telling you the truth .
[http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/](http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/)
The last supported release from this PPA was saucy .

Your sources need to be adjusted .

[INDENT][INDENT]it is what it ain't
[/INDENT][/INDENT]

---

### Post by Impavidus on 2017-02-24
Upgrading to 16.04 is not a way around this problem. You problem is that that PPA has not been maintained in years. It's not available for 14.04 nor for 16.04. Just disable the PPA and try and find your favourite software somewhere else. Or find an alternative.

---


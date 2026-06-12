---
title: "Release upgrade question"
date: 2014-07-10
forum: General Help
---

### Post by mikodo on 2014-07-10
I have read tonight, many reputable authors, including some on  Ubuntu Forums who are mods, say basically the same, (I apologize, I didn't save the links as I kept searching) as does [pablomme in his response to the question in the second response to the Original Poster's question: ]("http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade")

             "apt-get upgrade is restricted to the case  where packages are to be replaced by newer versions, but no package  needs to be added or removed. A new version of Firefox, for instance,  should be installable with apt-get upgrade.

  However apt-get upgrade will refuse to work when there are additions or removals required by the updated versions. For example, when you have kernel linux-image-3.2.0-10-generic installed and linux-image-3.2.0-11-generic appears, the linux-image-generic package gets updated to depend on the newer version. In order to install the new kernel, you need to run apt-get dist-upgrade.
  Notice how an apt-get upgrade will say that the kernel packages have been held back. That's the cue for using apt-get dist-upgrade."

So, I ran in my Xubuntu 12.04 just now, the following commands and as expected there was *no* offering, to upgrade to a newer release. Cool!

```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade
```

I always had thought before tonight, this would upgrade to a newer release:

```
sudo apt-get dist-upgrade
```

When I want to, (never have, I have always fresh installed), what are the commands to upgrade my system to a newer release, (like to Xubuntu 14.04)? I am going to try it for *fun*, before a fresh install of Xubuntu 14.04. Yes, all data I need, will be backed up and ready to sym-link, to the new fresh install.

A link would be great!

Thanks.

---

### Post by ian-weisser on 2014-07-10
```
$ do-release-upgrade
```

Try the manpage, too.

---

### Post by deadflowr on 2014-07-10
No fun, but from the horses mouth
man apt-get
 > upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

and
> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.


and then a release upgrade, which runs a completely different command
which is
```
do-release-upgrade
```
from the man do-release-upgrade

 > Upgrade  the  operating  system  to  the  latest  release from the com&#8208;
       mand-line.  This is the preferred command if the machine has no graphic
       environment  or  if the machine is to be upgraded over a remote connec&#8208;
       tion.


Don't know if any of this makes sense.

---

### Post by mikodo on 2014-07-10
Thanks, guys (er, folks). I work in a female dominated profession, and guys is used  generally.

I had read that in [Upgrading]("https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html") and in the man apt-get pages.

I guess I have my answers.

I'll look closer in the man pages.

):P

---


---
title: "apt-get dist-upgrade VS. apt-get upgrade"
date: 2008-03-06
forum: General Help
---

### Post by kesman on 2008-03-06
I really would like to know what's the difference between these two. I know that dist-upgrade WILL NOT upgrade ie. Ubuntu 7.10 to Hoary as someone would think, but do the exact same thing as upgrade.

From [https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto) :
> 
apt-get dist-upgrade - upgrades the entire system to a newer release. The same as the above, except add the &#8220;smart upgrade&#8221; checkbox -- i.e. tell APT to do whatever it has to do to upgrade to the latest packages, even if it means removing some other packages. (NB this is not a recommended way of upgrading to a new release)


This information is FAULTY as far as I know, never tested Hoary though, maybe APT is different in it.
EDIT:
Hoary being Hardy in this message =D

---

### Post by Distro Jockey on 2008-03-06
Well, umm, as Hoary is 5.04, I wouldn't consider that an upgrade from 7.10.
And seeing as 8.04 or 8.10 has not been released yet...

From the apt-get man file:

       update
           update is used to resynchronize the package index files from their sources. The indexes of available packages are fetched from the location(s)
           specified in /etc/apt/sources.list. For example, when using a Debian archive, this command retrieves and scans the Packages.gz files, so that
           information about new and updated packages is available. An update should always be performed before an upgrade or dist-upgrade. Please be
           aware that the overall progress meter will be incorrect as the size of the package files cannot be known in advance.

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of
           packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less
           important ones if necessary. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See
           also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

---

### Post by kesman on 2008-03-06
This doesn't give me any difference in upgrade or dist-upgrade.

Damn, Not Hoary, but Hardy =D

---

### Post by Distro Jockey on 2008-03-06
I guess that when 8.04 is released, it will.
That's the way I'm reading it.

Edit: Or maybe even 8.10 *shrugs*

---

### Post by Distro Jockey on 2008-03-06
> Damn, Not Hoary, but Hardy =D
I figured that's what you ment, but I think my point is still valid. :)
As a side note, I guess Hoary was too early to fit in with the current alphabetical animal name theme. :)
I vote for Jackal to succeed to Ibex. :)

---

### Post by tylerspaska on 2008-03-06
well, i'm not sure what it does, but it doesn't upgrade from 7.04 to 7.10, or anything else for that matter. i run 7.04 and i just did an apt-get dist-upgrade and nothing really happened. 

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

i've heard it does something to the repos.

---

### Post by kesman on 2008-03-06
Did you read my first post?

I've never seen any difference in apt-get upgrade and apt-get dist-upgrade, but since the Ubuntu documentary states, it should upgrade the version of ubuntu to the newest, but doesn't.

---

### Post by Distro Jockey on 2008-03-06
I did read the first post, as that was the post I first responded to.
I must admit, I have not tried a dist-upgrade, and I am still unclear as to what you are trying to upgrade from and to.
You probably need to look at adding the repo's for later versions than you are running.

---

### Post by kesman on 2008-03-06
I'm not trying to update anything, I was just curious since the documentary seems to be giving faulty information of the command, that's all. Also I'd like to know the difference between these two commands:'
```

apt-get upgrade
apt-get dist-upgrade

```
since they seem to do the same thing, and I can't figure out what the manpage means.

---

### Post by kuja on 2008-03-06
>       upgrade
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are
           currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages
           that cannot be upgraded without changing the install status of another package will be left at their current version. An update must be
           performed first so that apt-get knows that new versions of packages are available.

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of
           packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less
           important ones if necessary. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See
           also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

Straight from the manual :)

---


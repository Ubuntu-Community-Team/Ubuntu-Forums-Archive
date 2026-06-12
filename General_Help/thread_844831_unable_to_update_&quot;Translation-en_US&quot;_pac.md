---
title: "unable to update &quot;Translation-en_US&quot; packages"
date: 2008-06-29
forum: General Help
---

### Post by jrz on 2008-06-29
I installed Ubuntu 7.04 on my desktop a few months ago, and have since installed a few additional things using the Synaptic Package Manager. Recently, after clicking on the "Reload" button I also clicked on "Show progress of single files" and noticed that all packages which were listed as "Translation-en_US" returned a status of "Failed". I tried using several different repositories, all of which performed the same. I also tried using Adept Manager, and sudo apt-get update, which also fails. I've googled for answers to no avail, and tried the #ubuntu IRC channel, and even posted a Bug report  [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/243906](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/243906) and am at a total loss as to what to do next.

This is but one of several problems, but since it relates to retrieving up to date changes I feel it might be most important to resolve first. Any help would be appreciated.

---

### Post by Seisen on 2008-07-01
Its really nothing to worry about I get the same error all the time when I update my computer and it is completely up to date. To disable it so it doesn't come up any more go into /etc/apt/apt.conf and add this line to it

```
APT::Acquire::Translation "none";
``` then next time you update your computer the errors will disappear.

---


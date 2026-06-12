---
title: "Where can I find the package release schedule?"
date: 2016-06-01
forum: General Help
---

### Post by jistanidiot on 2016-06-01
I want to verify that a ton of packages were updated this evening, is there a website that lists what packages were updated and when?  I'm specifically interested in Ubuntu 14.04 LTS.

Thanks in advance.

---

### Post by vasa1 on 2016-06-01
I've used [http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/) in the past. I don't have a better link handy.

And if you're really interested in knowing what changed for a specific package, ```
sudo apt-get changelog <package-name> > ~/<package-name>-log
```will save a copy of the changelog for you to go through at leisure.

---

### Post by bearlake on 2016-06-01
> **vasa1 said:**
> I've used [http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/) in the past. I don't have a better link handy.

Was looking for this myself.
Thanks

---

### Post by howefield on 2016-06-02
And just to add, although you are probably already well aware, the log files in /var/logs/ will tell you what has been updated on your machine.

---


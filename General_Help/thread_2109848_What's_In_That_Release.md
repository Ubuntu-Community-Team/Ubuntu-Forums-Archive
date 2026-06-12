---
title: "What's In That Release?"
date: 2013-01-28
forum: General Help
---

### Post by ArlieS on 2013-01-28
Is there a web page or  similar I can use *from a non-linux system* to determine what package versions are in particular versions of ubuntu (12.04.01 and 12.10), and when/whether updates have been issued? 

I've got a non-functioning wubi installation, presently booted on windows, and I'd like to know whether there are interesting differences/changes in packages like grub-pc and grub-common, and whether there have been changes in the last fortnight. 

Also potentially interesting: a list of what packages are used in the course of booting a wubi system into ubuntu linux. grub-pc and grub-common are mentioned in past bug descriptions (something about changes that weren't backwards compatible, but not in 12.**) and I'm wondering what else might have been fixed in a non-backwards compatible manner. (E.g. perhaps my existing wubildr isn't right for whatever "sudo apt-get upgrade" might have done to me.)

---

### Post by snowpine on 2013-01-28
quick overview:

[http://distrowatch.com/ubuntu](http://distrowatch.com/ubuntu)

more detail:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Cheesemill on 2013-01-28
You can search the package database at [http://packages.ubuntu.com](http://packages.ubuntu.com)

Just make sure you select 'any' in the distribution drop-down if you want to see your search result across all versions.

For example the result for grub-common looks like [this]("http://packages.ubuntu.com/search?keywords=grub-common&searchon=names&suite=all&section=all").

---


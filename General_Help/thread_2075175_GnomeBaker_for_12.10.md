---
title: "GnomeBaker for 12.10"
date: 2012-10-23
forum: General Help
---

### Post by northwestern on 2012-10-23
Hi
Has anybody managed to install GnomeBaker in 12.10 yet?.

Regards
Northwestern

---

### Post by OzzyFrank on 2012-11-04
There is no version for Quantal 12.10, but I got it to install.

First add the PPA:

[B][COLOR="Red"]sudo add-apt-repository ppa:gnomebaker/stable
[/COLOR][/B]
Now you need to edit that source list:
[B][COLOR="Red"]
sudo gedit /etc/apt/sources.list.d/gnomebaker.list[/COLOR][/B]

... and replace both instances of ***quantal*** with ***oneiric***, then save/exit the file.

Next, run:

**[COLOR="Red"]sudo apt-get update[/COLOR]**

... and then:

[B][COLOR="Red"]sudo apt-get install gnomebaker
[/COLOR][/B]
You'll now have GnomeBaker back on your system!

---

### Post by mardybear on 2012-11-04
Thanks for the information.

Gnomebaker was always my favourite...always worked perfectly.

mardybear

---

### Post by dekoderek on 2012-11-11
**precise** would be probably more... precise, since it's newer than **oneiric**.

---

### Post by OzzyFrank on 2012-11-11
But is there one for Precise? When people were asking how to get GnomeBaker to install in 12.04, not long before Quantal was to be released, the Oneiric version was the last available. I think I did try using "precise" (along with "quantal") and had to change it to "oneiric" to get it to find the package for installation.

---

### Post by OzzyFrank on 2012-11-11
Looking in the official Ubuntu repos, the last version (officially) available is 0.6.4-1ubuntu1, for Lucid.

---

### Post by cb5online on 2013-01-03
Thank you for your help - your post has helped me too.

---


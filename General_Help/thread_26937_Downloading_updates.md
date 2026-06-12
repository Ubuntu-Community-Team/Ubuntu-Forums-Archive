---
title: "Downloading updates"
date: 2005-04-14
forum: General Help
---

### Post by mbourd25 on 2005-04-14
Hi Folks, I have a really good question concerning downloading updates. My problem is, at home, I only have a dialup connection and at work it's high speed internet.

Is their a way I could download the updates on my Windows workstation at work, copy those updates on my USB flash drive and bring them at home and use apt-get to point to my USB flash drive to install the updates or the new software?

Any help would be great. Thanks.

---

### Post by odix on 2005-04-14
Yes, its possible  :smile: 
copy the updates on your flash drive (download from update sites),
after insert the flash drive in your computer at home, copy the updates to a directory, change to that directory and execute:

dpkg-scanpackages ./ /dev/null | gzip > Packages.gz

you should point your /etc/apt/sources.list to the "update" directory.

there is a article in the german wiki [link](http://www.ubuntuusers.de/wiki/pakete:ubuntu-updates_pakete_auf_cd_sichern)

---

### Post by mbourd25 on 2005-04-14
Thanks Odix.

But how do I get the updates onto Windows so then I could copy them to my USB flash drive? What site should I go to to get the latest updates for Hoary?

Thanks.

---

### Post by odix on 2005-04-15
you may find some links in /etc/apt/sources.list

type at a prompt: cat /etc/apt/sources.list

regards

---


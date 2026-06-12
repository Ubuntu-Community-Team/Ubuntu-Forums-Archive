---
title: "Clone HDD installation to SSD"
date: 2014-02-12
forum: General Help
---

### Post by DimitrisC on 2014-02-12
My Asus U30JC-B1 laptop is starting to show its age! I was considering to replace it but Ubuntu 12.04 works so good on it that I don't want to spend months searching for a laptop that works just as well with Linux and also fit my budget.

So I decided that with some small upgrades I might extend the life of my Asus laptop for a few more months. I upgraded the ram to 8GB and purchased an SSD drive.

Since I spent countless hours tinkering with my Ubuntu installation and installing all kinds of applications I wanted to know if its possible to just clone the HDD existing installation to the new SSD drive so that the transition would be as seamless as possible. I know that the best option is to wipe and install on a clean drive but if there is a way to avoid this and still end up with a working SSD installation I would be more than happy to try that out first. Thank you.

---

### Post by crazymonkey05 on 2014-02-12
you should be able to copy your /home Directory which gots all your personal items. and move it to a new ubuntu install on the SSD as for intergrating it into the new system im not sure how to do it, though i know its possible.

---

### Post by oldfred on 2014-02-12
I also suggest a new install as some settings and configuration for a SSD need to be different anyway. 
Your /home has all your data & user settings. If you configured some hardware settings they are in /etc. And you can export a list of installed apps to make it easy to reinstall.

My backup is so I can easily do a new install and restore all the settings and configurations easily.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

If you do a copy, you have to reconfigure UUIDs, update fstab, reinstall grub and make a few other changes. And a new clean install auto housecleans all the cruft like log files, old kernels etc.


 Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

---

### Post by DimitrisC on 2014-02-13
Thank you so much! I will look into the info you provided.

---


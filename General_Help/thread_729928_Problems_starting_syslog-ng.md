---
title: "Problems starting syslog-ng"
date: 2008-03-20
forum: General Help
---

### Post by seeker1458 on 2008-03-20
OK, I am at a loss why I can't get syslog-ng to startup,
I have followed all the steps, and I can ./configure --enable dynamic linking, make and sudo make install.  But when I start trying to edit the .conf files, there are not to be found.  Nothing refering to syslog-ng in the following directories:

/etc/init.d/
/etc/default/
/usr/sbin/
/sbin/

The only trace that the installation has done anything at all (besides the files extracted from  the .tar.gz) is in /usr/local/sbin.  Why are none of the other files being created? Where should I start from here? You guys have been extremely helpful in the past. ALL HELP IS GREATLY APPRECIATED!

---

### Post by seeker1458 on 2008-03-20
.bump geez, 30 mins and already on page two?

---

### Post by seeker1458 on 2008-03-20
Well I solved it.  Simple enough...though I wonder if it would have worked without going and manually pulling down each individual library, compiler, and various other components.

sudo apt-get build-dep syslog-ng
sudo apt-get install syslog-ng

Then I checked in the system log, and it shows that syslog-ng is now started!

---


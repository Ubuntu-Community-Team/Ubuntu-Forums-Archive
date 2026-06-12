---
title: "[Ubuntu 14.04 LTS] Downgrade Asterisk to version 1.8?"
date: 2014-04-21
forum: General Help
---

### Post by matthys on 2014-04-21
After upgrading to Ubuntu 14.04 LTS my Asterisk is broken.
All Asterisk configuration files are for 1.8 and not for the new 11 version.
I tried to update my configuration to 11 but still no joy.

I wonder how I can downgrade Asterisk 11 to the previous version under Ubuntu 14.04 LTS.
I already tried: apt-get install asterisk=1:1.8.13.1~dfsg-3ubuntu3

But no joy. Any advise would be welcome.

Thanks,
Matthijs

---

### Post by TheFu on 2014-04-21
Asterisk is fickle.  Most people who do this professionally use pbx-in-a-box/stick and only do fork-lift upgrades.  They do NOT patch a running system ... er ... ever.

So - restore your old system until you've tested any newer asterisk to your satisfaction.  Is freeswitch an option?

---

### Post by matthys on 2014-04-22
Solved the problem by adjusting the configuration of Asterisk 11.

For those who wonder:
This was the original error message: No such label 'stdexten' in extension '6000' in context 'default'
In the default routing in extensions.conf I added this line as first entry under mentioned context label (in this case default);
**include = stdexten**

Restart Asterisk and all worked for me.

---


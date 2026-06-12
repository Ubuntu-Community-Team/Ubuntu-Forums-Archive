---
title: "Ubuntu server LTS question"
date: 2013-01-29
forum: General Help
---

### Post by billyboy1978 on 2013-01-29
Howdy.

In an Ubuntu LTS version, should I assume that postfix will be updated in its duration period?

---

### Post by snowpine on 2013-01-29
All packages will be updated with bug fixes and security patches for the life cycle of the release; that is the meaning of the word "support" in "long term support."

If you are curious what updates postfix received in 10.04 Lucid (the previous LTS) you might find this informative:

[http://changelogs.ubuntu.com/changelogs/pool/main/p/postfix/postfix_2.7.0-1ubuntu0.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/postfix/postfix_2.7.0-1ubuntu0.2/changelog)


And so far for 12.04 Precise:

[http://changelogs.ubuntu.com/changelogs/pool/main/p/postfix/postfix_2.9.1-4/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/postfix/postfix_2.9.1-4/changelog)

---

### Post by billyboy1978 on 2013-01-29
Thanx, 
If I do add some patches to postfix during install, do I have to repatch for each and every version? 
I'm thinking about the Quota patch..

If I've to repatch for every release, this'll take a lot of time..

---

### Post by tgalati4 on 2013-01-29
Probably.  The major version of postfix won't change during the support period, but there will be a few or several minor updates.  I'm not sure what exactly "quota" changes, but any library, support, or configuration files that get overwritten during the update will likely break the "quota" patch requiring a repatch.

It's not any different than running proprietary video driver that is partially compiled into the kernel.  Update the kernel and your graphics get broken until you recompile the proprietary driver and load it into the new kernel.

Perhaps there is a script to examine what gets changed with the quota patch.  That would reduce the agony units.  As a work-around, "pin" the version of postfix and only update postfix once a year--setting aside some down time to reapply and test the patch.

---


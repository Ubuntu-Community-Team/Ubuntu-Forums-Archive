---
title: "All GPG Keys Gone In My Ubuntu 14.04 LTS Trusty Tahr"
date: 2015-04-14
forum: General Help
---

### Post by mdavis1231 on 2015-04-14
Everything was perfect last night until I decided to install "Ubuntu After Install".  Now, after running that, all the GPG pubkeys for all of my PPA's are showing as missing when I run a "sudo apt-get update" in terminal.  I've tried using Y-PPA-MANAGER, it tells me it's restored them.  I also tried "launchpad-getkeys", and it told me that it had restored all the GPG keys.  Still nothing.  How do I get those keys to be recognized by my OS without having to completely reinstall? ](*,)

---

### Post by Bashing-om on 2015-04-14
mdavis1231; Hello;

Might try:
```

sudo apt-key update

```
which can fix missing Ubuntu keys.

If not, show that command and it complete output - between code tags - for our inspection and analysis .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]gotta start somewhere
[/INDENT][/INDENT]

---


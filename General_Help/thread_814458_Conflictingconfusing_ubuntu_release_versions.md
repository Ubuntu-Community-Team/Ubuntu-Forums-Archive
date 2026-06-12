---
title: "Conflicting/confusing ubuntu release versions?"
date: 2008-05-31
forum: General Help
---

### Post by supremedalek on 2008-05-31
I decided to update the ubuntu version in my laptop from 7.10 to 8.04 by wiping the HD and then doing a full install, with repartitioning and all that exciting stuff. That seemed to have gone fine -- I am typing this from the said machine -- but then I am finding conflicting info regarding the OS release I have:

```
raub@monaco:~$ head /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
raub@monaco:~$ cat /etc/debian_version 
lenny/sid
raub@monaco:~$ 

```

Who is telling the truth and who is not? And, why is that happening?

---

### Post by mikewhatever on 2008-05-31
What's conflicting with what? Ubuntu is based on Debian and the only Ubuntu version you have is Hardy.
[Ubuntu and Debian]("http://www.ubuntu.com/community/ubuntustory/debian")

---


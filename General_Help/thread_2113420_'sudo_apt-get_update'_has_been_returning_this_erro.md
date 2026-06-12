---
title: "'sudo apt-get update' has been returning this error"
date: 2013-02-07
forum: General Help
---

### Post by FOSSteror on 2013-02-07
*) 'sudo apt-get update' has been returning this error -


""" W: Failed to fetch [http://ppa.launchpad.net/natesm/ease/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/natesm/ease/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/natesm/ease/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/natesm/ease/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. """

*) HINT :: I found that from the above URL, the 'quantal' doesn't exist. I mean - the URL is valid only till -- 

"" [http://ppa.launchpad.net/natesm/ease/ubuntu/dists](http://ppa.launchpad.net/natesm/ease/ubuntu/dists) "" after which 'quantal' doesn't exist

*) QUESTION: Kindly let me know --> the reason for the missing 'quantal' and --> why it was ok once but not now..                        Also, --> how am I expected to protect myself from falling into such errors in future

---

### Post by ibjsb4 on 2013-02-07
There is no package offered for your system, remove it.

[http://ppa.launchpad.net/natesm/ease/ubuntu/dists/](http://ppa.launchpad.net/natesm/ease/ubuntu/dists/)

If you want to protect myself from falling into such errors in future, stick with the official repo's (software center).  PPA's can be hit and miss.

---

### Post by fantab on 2013-02-07
It is giving that error because [http://ppa.launchpad.net/natesm/ease/ubuntu/dists/](http://ppa.launchpad.net/natesm/ease/ubuntu/dists/) does not exist any more or it is faulty... Just remove that particular ppa from your sources as suggested by #2. You can do this by editing sources.list using the **Software Sources** utility. Then run update.

---


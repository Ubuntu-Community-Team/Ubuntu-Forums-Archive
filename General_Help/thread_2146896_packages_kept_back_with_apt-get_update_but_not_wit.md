---
title: "packages kept back with apt-get update but not with update manager?"
date: 2013-05-20
forum: General Help
---

### Post by Mickser_52 on 2013-05-20
I have been meaning to ask this question for a long time now. I usually use the terminal...  apt-get update&apt-get upgrade command to check for updates every morning. Some times, as this morning, the message appeared that some packages are being kept back. I assume there is some reason for this.

What I cannot understand is if I use the update manager to update it updates everything including those that the apt-get command kept back.

Perhaps somebody can the explain the difference.

I am using ubuntu 12.04 on an Asus k55v.

---

### Post by Irihapeti on 2013-05-20
The packages being held back when you use apt-get update are new packages that are going to be installed. So I suppose you could that they aren't strictly speaking updates.

To install all the updates from the command line and have nothing held back, use
```
sudo apt-get dist-upgrade
``` or
```
sudo apt-get dselect-upgrade
```
Contrary to what you might think, the first one doesn't take you to the next Ubuntu version.

So, presumably update-manager is actually doing apt-get dist-upgrade in the background.

---

### Post by Mickser_52 on 2013-05-20
Many thanks for your reply. I am still not 100% clear on the distinction between upgrade and dist-upgrade but that does appear to be what the update manager does.

---

### Post by ibjsb4 on 2013-05-20
This may help

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by hs-bakhtiari on 2013-11-12
thanks alot , it worked for me .
i wondered why update manager and apt-get upgrade results are different and usually the command result was less than update manager but
using apt-get dist-upgrade solved my problem

---

### Post by philinux on 2013-11-12
> **hs-bakhtiari said:**
> thanks alot , it worked for me .
i wondered why update manager and apt-get upgrade results are different and usually the command result was less than update manager but
using apt-get dist-upgrade solved my problem

That's not quite right now.  Software updater uses phased updates. 10% users at a time to make sure there are no regressions.

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

[http://qa.ubuntu.com/2013/08/07/phasing-of-stable-release-updates/](http://qa.ubuntu.com/2013/08/07/phasing-of-stable-release-updates/)

---


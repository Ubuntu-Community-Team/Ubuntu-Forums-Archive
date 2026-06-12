---
title: "Xubuntu Update"
date: 2014-10-18
forum: General Help
---

### Post by Quarkrad on 2014-10-18
Running 13.04 and need to upgrade.  Before I advise friend how to do this I wanted to test on my machine via Virtualbox (I appreciate she has different hardware so results may well be different).  On my virtualmachine (host = ubuntu 14.04   guest = xubuntu 13.04)  I can launch xubuntu and get an internet connect and surf the web.  However, the system software update environment cannot connect and keeps asking me check my internet connection (which I know is OK).  I have tried sudo apt-get update but keep coming back to this loop.  Any ideas on how to overcome this much appreciated.

---

### Post by mikewhatever on 2014-10-18
Check out this: [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release).

---

### Post by Quarkrad on 2014-10-18
Thanks. 1 Answer says:

[B] The safest way to upgrade from 13.10 to 14.04 is by doing the following in a Terminal, thus:

a) do a CTRL + ALT + T to open a Terminal

b) type the following commands:

sudo apt-get update

to update your packages lists

sudo apt-get dist-upgrade[/B]

But I cannot do this because I know that if I type sudo apt-get update I get told I have no internet connection.

---

### Post by mikewhatever on 2014-10-18
That particular answer is incorrect, so don't get stuck on it. You need to change the sources first.

I suppose the link I had in mind was this: [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release). (Fixed above as well.)

---


---
title: "Error During Upgrade From 11.10"
date: 2013-01-15
forum: General Help
---

### Post by RWhitney on 2013-01-15
On my Ubuntu 11.10 installation I did an "apt-get dist-upgrade" to upgrade to the next version of Ubuntu, however it was taking quite a while and I went to sleep, when I came back to my computer now 12 hours later the upgrade had locked up on me.

I closed out the terminal window and opened up a new one.
I made sure to remove the locks on directories, and ran "dpkg --configure -a"

I just want to know that:
A. I handled the situation properly.
B. My computer will reboot fine after all this.
C. There is nothing I am missing.

Can somebody please verify that these were the correct steps and let me know if there is anything more that needs to be done to fix this issue?

---

### Post by plucky on 2013-01-16
> **RWhitney said:**
> On my Ubuntu 11.10 installation I did an "apt-get dist-upgrade" to upgrade to the next version of Ubuntu, however it was taking quite a while and I went to sleep, when I came back to my computer now 12 hours later the upgrade had locked up on me.

I closed out the terminal window and opened up a new one.
I made sure to remove the locks on directories, and ran "dpkg --configure -a"

I just want to know that:
A. I handled the situation properly.
B. My computer will reboot fine after all this.
C. There is nothing I am missing.

Can somebody please verify that these were the correct steps and let me know if there is anything more that needs to be done to fix this issue?


The "apt-get dist-upgrade" command will not get you to 12.04,all it will do is install the latest updates.

To do a distribution upgrade see [Here](https://help.ubuntu.com/community/PreciseUpgrades)


Good Luck

---

### Post by Warren Hill on 2013-01-16
Take a look here: [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

If you are having any difficulties I recommend getting or creating a CD/Bootable USB and doing a clean install from that.  Make sure you backup first.

---


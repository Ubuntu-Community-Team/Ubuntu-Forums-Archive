---
title: "Is it possible to install a framework made for Ubuntu 16.04 on 17.04?"
date: 2017-08-23
forum: General Help
---

### Post by gauss4563 on 2017-08-23
Hi,

I need to install ROOT 6.10 framework ([https://root.cern.ch/content/release-61002](https://root.cern.ch/content/release-61002)) and the suggested OS is Ubuntu 16 (gcc5.4) or 14 (gcc4.8) and I would like to know whether it is possible to install it on Ubuntu 17? 
Is there any special reason why it won't work or will be considerably less stable?

Thanks in advance!

---

### Post by Autodave on 2017-08-23
I can't answer your question, but keep in mind that if you upgrade to 17.04 that means that you will have to upgrade to 17.10 in another month or two. And then to 18.04 in another 6 months. 

   Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

While an upgrade to the next version *should *go without a problem, I find that it rarely does.

---

### Post by gauss4563 on 2017-08-23
Thanks for the advice!
Why is upgrading so problematic?

---

### Post by ajgreeny on 2017-08-23
> **gauss4563 said:**
> Thanks for the advice!
Why is upgrading so problematic?
For some it's not a problem and all goes as smooth as silk; for others everything goes completely "to worms" when doing an update.
I think it depends how near a default installation you are using and how much customisation of setup, etc etc.

I have a separate /home partition on my main machine which makes clean installation simple, and a lot faster than upgrading, so I have never upgraded from one distro version to the next in my 12 years of using Ubuntu.  Your situation may be different and you may like to attempt upgrading the distro, and may find it works fine for you. However, I would plead with you to ensure you have good restorable backups of all your personal files before doing so.

---


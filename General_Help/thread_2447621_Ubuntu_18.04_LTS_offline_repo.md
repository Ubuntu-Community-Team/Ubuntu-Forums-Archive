---
title: "Ubuntu 18.04 LTS offline repo"
date: 2020-07-22
forum: General Help
---

### Post by wazzu62 on 2020-07-22
Somewhat new to ubuntu - so bear with me.

I have some system that are not connected to the internet the I need to be able to easily add packages to.  I would like to stand up a local repo on on of the systems.
I am looking at this guide [https://help.ubuntu.com/community/AptGet/Offline/Repository?action=show&redirect=SuiteCodename](https://help.ubuntu.com/community/AptGet/Offline/Repository?action=show&redirect=SuiteCodename)

Questions.  Can I use wget with --recursive --no-parent to just download everything?  (bionic, bionic-security, bionic-updates)

Any help with getting this going would be greatly appreciated.

TIA

---

### Post by Tadaen_Sylvermane on 2020-07-22
That seems to be very old and manual. Check out the apt-mirror package. Set a single config file and run it whenever is convenient.

---


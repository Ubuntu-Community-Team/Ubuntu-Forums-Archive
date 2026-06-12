---
title: "How to get rid of [ 4.321539] systemd[1]: Failed to find module 'autofs4'"
date: 2020-11-03
forum: General Help
---

### Post by manmath on 2020-11-03
Dear members, I have neither autofs package nor autofs4 kernel module. I don't need it. Please suggest how to get rid of the following systemd message that shows during booting:

[    4.321539] systemd[1]: Failed to find module 'autofs4'

---

### Post by ActionParsnip on 2020-11-03
Possibly this bug
[https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/1824333](https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/1824333)
Are you using the HWE kernel? 
Does syslog get spammed with these or is it just a one off each boot?

---

### Post by manmath on 2020-11-03
The error shows just once while booting. And I'm not using HWE kernel. And the bug has nothing to do with my problem as I've not installed autofs package. Also my custom kernel doesn't have autofs4 module. All I want is to get rid of that error message and save a few seconds. I believe there must be a config file that systemd reads to load autofs4 module, and there must be a way to delete or comment out autofs4 so that systemd won't look for that module. The crux is tell me ways/fixes/workarounds that can make systemd not look for autofs4.

---


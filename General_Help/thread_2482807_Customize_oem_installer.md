---
title: "Customize oem installer"
date: 2023-01-11
forum: General Help
---

### Post by elementcz on 2023-01-11
I would like to customize the ubiquity installer (used during setup of Hyper-V Ubuntu machine) to integrate some things like creation of user account based on SSO login, check the user password based on standard settings (pam/pwquality/etc). 
I already have some small changes integrated (like password check against pwquality.conf) but I have hard time to develop something more complicated - the first thing is that I had no luck to find some source of information how to do that properly ie. source code (at this moment I'm patching the original installer during creation of custom image), the second thing is to have some guide how to develop/debug this on live machine without need to go through new installation (or using snapshots) all the time.

Is there some guide for ubiquity/oem installer developers or is it recommended to focus on some other installer app?
Thx

---

### Post by dragonfly41 on 2023-01-11
Perhaps CUBIC might help with ISO customisation.
And/or automation scripts for DevOps.

---


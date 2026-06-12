---
title: "Edit MOTD file for ssh to run shell script or something similar..."
date: 2014-05-11
forum: General Help
---

### Post by Jonathan_J on 2014-05-11
Greetings,

I am trying to edit my MOTD file... I have the update-motd application installed, but when I have a two-factor program (Duo) that pulls the MOTD, it just pulls the MOTD text file instead of the update-motd stuff I have edited.  Does anyone have any workarounds for this issue or suggestions they can provide to get this working for me?

Appreciate the help!

---

### Post by tgalati4 on 2014-05-11
Perhaps:

libpam-modules - Pluggable Authentication Modules for PAM
update-motd - superceded by pam_motd in libpam-modules

I would undo the changes to update-motd and read up on what services pam_motd offers.

tgalati4@Mint14-Extensa ~ $ apropos motd
motd (5)             - message of the day
motd.tail (5)        - Template for building the system message of the day
pam_motd (8)         - Display the motd file
update-motd (5)      - dynamic MOTD generation

```
man pam_motd
```

I'm not familiar with duo, but it looks like it is part of PAM as well:

tgalati4@Mint14-Extensa ~ $ apt-cache search duo
python-cddb - Python interface to CD-IDs and FreeDB
texlive-pictures - TeX Live: Graphics packages and programs
dimbl - Distributed Memory Based Learner
libduo-dev - Duo Security development libraries and header files
libduo3 - Duo Security library
libpam-duo - PAM module for Duo Security two-factor authentication
login-duo - login wrapper for Duo Security two-factor authentication

Perhaps describe what your script is supposed to do.  There are probably several ways to accomplish the task.

---


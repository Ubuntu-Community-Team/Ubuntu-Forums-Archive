---
title: "Warning when doing a ubuntu upgrade with update manager"
date: 2007-09-11
forum: General Help
---

### Post by tc101 on 2007-09-11
Using the update manager, when I go to install updates, I get a message saying:

 "Warning, you are about to install software than can't be authenticated"

This is the stuff was going to installed in the upgrade.  Is there a problem?

k3b (version 1.0-0ubuntu2) will be upgraded to version 1.0-0ubuntu2+medibuntu1
libk3b2 (version 1.0-0ubuntu2) will be upgraded to version 1.0-0ubuntu2+medibuntu1
libkrb53 (version 1.4.4-5ubuntu3.1) will be upgraded to version 1.4.4-5ubuntu3.3
gawk (version 1:3.1.5.dfsg-4build1) will be installed
libavcodec0d (version 3:0.cvs20060823-3.1ubuntu4+medibuntu2) will be installed
libdc1394-13 (version 1.1.0-3ubuntu2) will be installed
libdvdcss2 (version 1.2.9-2medibuntu2+build1) will be installed
libfame-0.9 (version 0.9.1-0.2) will be installed
libpostproc0d (version 3:0.cvs20060823-3.1ubuntu4+medibuntu2) will be installed
libpvm3 (version 3.4.5-7) will be installed
transcode (version 2:1.0.2-0.8ubuntu3) will be installed

---

### Post by Happy_Man on 2007-09-11
All that means is that you are using non-Ubuntu supported repos, and that they cannot guarantee the safety or usability of them, and that Ubuntu is not liable for anything that happens because of software installed using them. 


Go ahead and use them anyway. Medibuntu repos are harmless.

---

### Post by mcduck on 2007-09-11
Did you add the Medibuntu's gpg key when adding those repositories? If you didn't, do that now with the following command:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

---


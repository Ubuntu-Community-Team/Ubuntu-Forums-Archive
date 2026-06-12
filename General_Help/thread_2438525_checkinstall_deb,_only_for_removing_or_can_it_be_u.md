---
title: "checkinstall deb, only for removing or can it be used for installing?"
date: 2020-03-13
forum: General Help
---

### Post by u666sa on 2020-03-13
I compiled CoreCtrl latest on Ubuntu 18.04 LTS [https://www.upload.ee/files/11263385/corectrl_build_20200313-1_amd64.deb.html](https://www.upload.ee/files/11263385/corectrl_build_20200313-1_amd64.deb.html)
Is it good only for uninstalling or can it be installed by anyone with Ubuntu 14.04??

---

### Post by monkeybrain20122 on 2020-03-13
It can be installed if the other 14.04 meets the dependencies. But 14.04 has long passed eol. Update your OS.

---

### Post by u666sa on 2020-03-13
No no, 18.04 LTS

---

### Post by ajgreeny on 2020-03-13
The standard procedure is to run the following commands from within the folder containing the source files, though the configure and make part could be different depending on what the **install** or **readme** file says.
[LIST=1]
[*]./configure
[*]make
[*]sudo checkinstall
[/LIST]
Having used **checkinstall** instead of just **install** as the final command means that the .deb package file will be placed in the source folder, allowing you to uninstall with usual apt commands or synaptic, if you use that, and then reinstalled again using the .deb package.
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

There are, however, a few who doubt its security, see [https://askubuntu.com/questions/1138384/why-is-checkinstall-no-longer-being-maintained](https://askubuntu.com/questions/1138384/why-is-checkinstall-no-longer-being-maintained), though I can't comment more on that, not knowing enough about its use.

---


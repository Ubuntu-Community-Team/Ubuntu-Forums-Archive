---
title: "A system restart is needed to complete the update process"
date: 2017-04-07
forum: General Help
---

### Post by scottbomb on 2017-04-07
I have Kubuntu 16.04 running on a few systems. Here lately, I'm getting these notifications that my computer needs to be restarted to complete the update process. My question is, why is the computer updating itself in the first place? I didn't run apt-get update/upgrade so I shouldn't be seeing this message. 

Am I missing something here?

---

### Post by Keith_Helms on 2017-04-07
Go look at "software and updates".  Under the Updates tab on the line "When there are security updates:", do you have it set to "Download and install automatically"?

---

### Post by TheFu on 2017-04-07
Might you have selected "automatic security patches" during the installation?
[https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html) - non-GUI specific.
[https://askubuntu.com/questions/45797/fully-automatic-updates-in-kubuntu](https://askubuntu.com/questions/45797/fully-automatic-updates-in-kubuntu) - ubuntu specific.

---

### Post by scottbomb on 2017-04-07
> **Keith_Helms said:**
> Go look at "software and updates".  Under the Updates tab on the line "When there are security updates:", do you have it set to "Download and install automatically"?


That was it! Thank you.

---


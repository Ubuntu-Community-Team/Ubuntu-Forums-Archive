---
title: "Removing Bionic start up scripts."
date: 2015-02-01
forum: General Help
---

### Post by couch2 on 2015-02-01
All,

I'm running 14.04.

About a year ago, I installed the Bionic Client in order to help with some distributed computing.  Due to the nature of the application, my processor was consistently running at 100%, which isn't a big thing but, my cpu fan constantly ran.  I don't want to burn the sucker out.

I've been able to stop the daemon from running but I was wondering if some of you could help me either modify the existing scripts -- there are sever within the 'rc' directories.  I'm not sure if I can simply remove them or rename them a certain way to stop this from starting up.

My apologies, I'm still fairly new to Linux even though I've run it successfully on my laptop for sever years now.  Any help would be greatly appreciated.


Couch

---

### Post by ian-weisser on 2015-02-01
Do not rename files placed by the package manager - it can cause terrible, terrible problems.

If you are not going to use the client in the immediate future, another solution is to simply uninstall the program until you want to try it again.

---


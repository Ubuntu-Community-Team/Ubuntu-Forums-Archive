---
title: "Attention: wubi uninstaller may erase your data"
date: 2008-06-02
forum: General Help
---

### Post by billbear on 2008-06-02
There is a problem in wubi uninstaller that may cause data loss.
Wubi uninstaller checks the partitions and finds the first partition that contains a "ubuntu" folder, then erases that folder. 
This is bad when someone has other folders with the same name "ubuntu" under other drive letters.
A user posted at the chinese ubuntu forum that he had a "ubuntu" folder under drive G: which contains his documents, and the wubi installation was at J:\ubuntu. When he uninstalled wubi, the ubuntu folder at drive G: was removed and J:\ubuntu was left untouched. (Unfortunately G: comes first)
The post can be found here:  [http://forum.ubuntu.org.cn/viewtopic.php?t=117746](http://forum.ubuntu.org.cn/viewtopic.php?t=117746)
I confirmed this bug in a virtual machine and i consider it a serious bug.


[https://bugs.launchpad.net/ubuntu/+bug/236741](https://bugs.launchpad.net/ubuntu/+bug/236741)

---

### Post by ago on 2008-06-02
confirmed, will be fixed in next release

---

### Post by skyx on 2008-06-02
[https://bugs.launchpad.net/ubuntu/+bug/236741](https://bugs.launchpad.net/ubuntu/+bug/236741)

---


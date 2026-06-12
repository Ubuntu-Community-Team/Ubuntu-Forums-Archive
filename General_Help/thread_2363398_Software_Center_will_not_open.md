---
title: "Software Center will not open?"
date: 2017-06-09
forum: General Help
---

### Post by andreadixon825 on 2017-06-09
Hello, I just upgraded and now my software center is not opening. the mouse car sol just has a loading then it goes away, Should I just uninstall it, and then reinstall. never had this problem on 16. but know I cant open it. Thank you

---

### Post by monkeybrain20122 on 2017-06-09
Which xubuntu version? Yes, it doesn't start in Ubuntu 17.04. It does start in 16.04 but not sure if it works since I never use it. synaptic is a much better package manager

if you have occasions to install download .deb packages, use gdebi
```
sudo apt install synaptic gdebi
```

You don't need to uninstall it as it is probably part of your desktop environment and it may remove packages you don't want removed. Just leave it alone and don't use it.

---


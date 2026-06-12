---
title: "GUI authentication Error"
date: 2018-11-05
forum: General Help
---

### Post by us02 on 2018-11-05
Hi,
I can't perform superuser tasks on GUI. For example, installing a local deb file or using update-manager via GUI. It successfully checks for updates, when I click "install", it crashes the moment it is supposed to ask for the password. The terminal works just fine.
Any solutions? Thanks
OS = Ubuntu 18.04.1

---

### Post by #&amp;thj^% on 2018-11-05
This request is a bit vague, at least to me.
Open a terminal and please run:
```
update-manager
``` 
and if there are any updates, try install them posting back the return from the terminal.
Please use code tags or use[ ubuntu pastebin]("https://paste.ubuntu.com/") to post the results.
This way we may have a better chance to help you.

---

### Post by us02 on 2018-11-08
I can open update manager. But it checks for updates, ask me to install, when I click install now it crashes after Waiting for authentication.
However, it works fine if I run it with sudo i.e. sudo update-manager

---


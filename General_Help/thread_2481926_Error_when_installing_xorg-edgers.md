---
title: "Error when installing xorg-edgers"
date: 2022-12-13
forum: General Help
---

### Post by luncaaa on 2022-12-13
Hello o/

I installed xorg edgers using the command **sudo add-apt-repository ppa:xorg-edgers/ppa**, but an error will appear when running **sudo apt update **afterwards.
(it's xorg-edgers, although the forum will transform the **:** and **x** into that face)

This is the error:
```
Ign:11 https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu jammy InReleaseErr:12 https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading packages list... Done
E: The repository «https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu jammy Release» does not have a Publisher file.
N: You cannot safely update from a repository like this and so it is disabled by default.
N: See the apt-secure(8) manual page for details on creating repositories and configuring users.
```

I tried removing the PPA and adding it again, although I have the same problem. What can I do to fix it?

---

### Post by deadflowr on 2022-12-13
The PPA is dead so don't use or add it anymore.
There is no fix.
Dd you have need for updated X packages or something?

> (it's xorg-edgers, although the forum will transform the : and x into that face)
If you click on Go Advanced and scroll down there is a feature to turn off smileys in text.
i have done so for you.
I think any output posted in code tags will also remove smileys.

---

### Post by luncaaa on 2022-12-15
Hey o/

I didn't know it was dead. I didn't need to update anything specifically, I just wanted to check if there was anything else I could update.
Thanks for your reply and "fixing" the emoji thing!

---


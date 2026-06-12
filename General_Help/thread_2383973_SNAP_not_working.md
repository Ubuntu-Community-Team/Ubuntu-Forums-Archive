---
title: "SNAP not working"
date: 2018-01-31
forum: General Help
---

### Post by warmango on 2018-01-31
Basically, I am trying to install Anbox. one issue, I run the command 
```
sudo snap install --classic anbox-installer
```
but when I try to run the command, I get this error

```
Zach@duncan:~$ sudo snap install --classic anbox-installer
error: cannot communicate with server: Post http://localhost/v2/snaps/anbox-installer: dial unix /run/snapd.socket: connect: no such file or directory
```

---

### Post by #&amp;thj^% on 2018-01-31
What happens with code:
```
snap run anbox-installer
```

---

### Post by mc4man on 2018-01-31
See 
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1631514](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1631514)

---

### Post by cruzer001 on 2018-01-31
To add to mc4man's post

Had a look at this package (online) and there seems to be several things that can go wrong.

The site support stops at ubuntu 17.04
Not only snap, but snapd needs to be installed
No 32bit support
Looks like its still in alpha
The install instructions require more than just the one package (if I read this right)
PPA does not support ubuntu 17.10

Have you read any of this?

[https://github.com/anbox/anbox/wiki/Installation](https://github.com/anbox/anbox/wiki/Installation)
[https://launchpad.net/~morphis/+archive/ubuntu/anbox-support](https://launchpad.net/~morphis/+archive/ubuntu/anbox-support)
[https://github.com/anbox/anbox/issues/146](https://github.com/anbox/anbox/issues/146)
[https://askubuntu.com/questions/944238/anbox-install-problem/944245](https://askubuntu.com/questions/944238/anbox-install-problem/944245)

Haven't used snap yet, but I guess it offers just a package and no package info or depends.  Hope I'm wrong on that.

---


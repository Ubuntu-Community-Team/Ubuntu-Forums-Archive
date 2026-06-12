---
title: "Visudo NOPASSWD doesn't work"
date: 2007-11-09
forum: General Help
---

### Post by azenz on 2007-11-09
I try to enable some apps to be run as sudo with root privileges without having to enter the password and so edited the sudoers file, adding my_user_name ALL= NOPASSWD: /usr/sbin/script_name (with my real name and script name). I just doesn't work and this is really annoying. By the way I know why I want to do this and the risks involved.

---

### Post by agrippas on 2007-11-11
Try correcting the line order as in here: [https://lists.ubuntu.com/archives/ubuntu-users/2004-December/017251.html](https://lists.ubuntu.com/archives/ubuntu-users/2004-December/017251.html)

---

### Post by azenz on 2007-11-11
Thanks, the problem was actually not with visudo but with me having to put "bash" before calling the script which confused things it seems, now I put #!/bin/bash at the beginning of the script to handle that and visudo works.

---


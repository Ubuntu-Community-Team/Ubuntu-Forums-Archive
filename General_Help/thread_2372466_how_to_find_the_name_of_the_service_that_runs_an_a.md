---
title: "how to find the name of the service that runs an application"
date: 2017-09-25
forum: General Help
---

### Post by linux.girl on 2017-09-25
Hi everyone,

Silly question: how to find the name of the service that runs an application ? For example, the name of the service that runs ssh is sshd, http is httpd and so on. But if I don't know the name, is there a cmd to find out?

Thanks!

---

### Post by SeijiSensei on 2017-09-25
On machines before 16.04 which used SysV init scripts, all the startup/shutdown scripts appear in /etc/init.d/ so you can find their names there.  Starting with 16.04, Ubuntu uses systemd.  To see the list of available services, run
```
sudo systemctl list-unit-files
```

---

### Post by linux.girl on 2017-09-26
Thanks!!!!

---

### Post by vasa1 on 2017-09-26
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by linux.girl on 2017-09-26
I marked it as solved :-)

---


---
title: "Failing to start services on Ubuntu 8.04"
date: 2008-05-23
forum: General Help
---

### Post by peter24 on 2008-05-23
I have 2 weeks old lenovo T61 laptop. Was happily running ubuntu 8.04 all this time.
I didn't reboot for a week or so. Today after installing updates, I rebooted, and it failed to start. It hangs starting sshd, killing the process that starts sshd, just brings another service to start that also hangs in the same manner. 
strace shows init script doing a wait:
"wait4(-1, <unfinished ...>"
a strace on the process running /usr/sbin/sshd hangs and sending interrupt doesn't do anything.
also, for example running ifconfig hangs too.

Besides getting updates, I can't think of anything what would cause it. But I am writing it on another ubuntu 8.04 running fine, rebooted today with all the updates... not to mention the rest of the ubuntu community.

Any hints/help will be greatly appreciated.

---


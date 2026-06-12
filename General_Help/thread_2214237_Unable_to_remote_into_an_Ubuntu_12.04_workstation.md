---
title: "Unable to remote into an Ubuntu 12.04 workstation"
date: 2014-03-31
forum: General Help
---

### Post by Vannyi on 2014-03-31
I have setup an Ubuntu 12.04 workstation.  I then went into the Desktop Sharing Preferences and under sharing, enabled:

1.  Allow other users to view your desktop
2.  Allow other users to control your desktop.

When I try and remote into this workstation using the Remote Desktop Client, I get the error message "error 10.1.1.14 - Unable to connect".  I can however ping the workstation from a terminal session.

Any thoughts on what I'm missing?

Thank you

---

### Post by sudodus on 2014-03-31
Are you running a server daemon for ssh? Check for sshd with

```
ps -A|grep sshd
```

If not I suggest that you install openssh-server. See this link

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---


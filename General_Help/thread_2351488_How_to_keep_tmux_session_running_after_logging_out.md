---
title: "How to keep tmux session running after logging out"
date: 2017-02-03
forum: General Help
---

### Post by waltman on 2017-02-03
I just discovered that systemd kills my tmux session when I logout. I remember hearing that they were adding this "feature" last year, and I see some discussions online from last May about various ways to keep it from doing so. What I can't find is if it was ever resolved. Now that it's been in place for a while, is there a consensus as to the best way to disable it?

---

### Post by 1clue on 2017-02-03
Have you tried ctrl-b d?

---

### Post by waltman on 2017-02-03
I definitely closed my terminal window, but to be honest I'm not 100% sure I detached from tmux, too. I'd try it again, but I don't feel like having to restore all my irssi channels again :)

---

### Post by deadflowr on 2017-02-04
I believe you are talking about this bug:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=825394]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=825394")

---

### Post by waltman on 2017-02-07
Yes, that's one of the many discussions that were made online at the time. While I have my own opinions on the matter, I'm not interested in rehashing things. I'm just curious if there's a consensus on the best way to disable it.

---

### Post by 1clue on 2017-02-07
Really me too. I don't think I have any systemd-running remotes right now, and I'm damned if I'm going to install any until such time as I know there's a fix to this.  My entire day is spent inside of tmux sessions on remote boxes. They MUST stay running after logout.

---

### Post by Kastagir on 2017-03-20
I'm having the same problem (Ubuntu 16.10). Anyone found the solution?

---

### Post by kvidell on 2018-02-20
17.10, still happening. I've adjusted /etc/systemd/logind.conf in the appropriate ways, and it's still a problem.

---


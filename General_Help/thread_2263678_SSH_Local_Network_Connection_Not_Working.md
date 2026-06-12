---
title: "SSH Local Network Connection Not Working"
date: 2015-02-02
forum: General Help
---

### Post by sam64 on 2015-02-02
I've got both my laptop (with my Ubuntu VM on it) and my desktop (to be the server) connected to the same Ethernet Adapter, so I'm fairly certain that I'm using a local network connection. I've already confirmed that the ip address of my desktop is correct, but I'm still unable to connect:
[ATTACH=CONFIG]259668[/ATTACH]
I don't understand. Am I putting the ip address in the wrong place? Under the Basic tab, am I supposed to use the Username and Password for my desktop computer's user account, or some other account? Do I need to specify anything under the SSH tab?

---

### Post by newbie-user on 2015-02-04
You only use the SSH tab if you're creating an SSH tunnel. For basic RDP, you just need the hostname or ip, username, and password. Make sure that you add User to the list of allowed RDP users on your Windows box.

---


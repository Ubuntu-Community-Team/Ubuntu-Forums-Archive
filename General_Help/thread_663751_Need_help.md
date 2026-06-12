---
title: "Need help"
date: 2008-01-10
forum: General Help
---

### Post by onion221 on 2008-01-10
I never get prompted for a password anymore. I can install updates and software without being prompted as well. I checked my users and groups and it seems the root account was the first one on the list instead of second. I find that odd because on my other gutsy comps its vice versa. Any help?

---

### Post by cdenley on 2008-01-10
I think what you are referring to is that once you enter your password, you will have admin privileges for a certain amount of time (I think 15 minutes by default). If you want to force yourself to enter a password before your previous authentication times out, you can run "sudo -k". You can change your settings so you are always prompted for a password by editing sudoers (sudo visudo), and adding timestamp_timeout=0 to your defaults line so it looks like

```

Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0

```

---


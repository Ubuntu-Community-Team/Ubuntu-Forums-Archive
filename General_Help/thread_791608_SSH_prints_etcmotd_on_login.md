---
title: "SSH prints /etc/motd on login"
date: 2008-05-12
forum: General Help
---

### Post by jambalaya on 2008-05-12
Hi.
When I login to my remote computer running Kubuntu 8.04 x64 (clean install), the system prints the contents of the /etc/motd file contents. I also have another Kubuntu 8.04 bok (32bit, upgraded from 7.10), and this one doesn't print this text. How can I diable this motd printing, then, without deleting this file's contents (this must have been disabled by default somehow since the "older" Kubuntu doesn't print it)?
Thanks.

---

### Post by Monicker on 2008-05-12
Look at the PrintMotd line in /etc/ssh/sshd_config

You will need to reload or restart ssh for changes to take effect.

```
sudo /etc/init.d/ssh reload
```

---

### Post by jambalaya on 2008-05-12
How could I have missed that! Thanks for your answer.

---

### Post by Atreus12 on 2008-06-05
Sorry for bringing up old threads, I found this while searching for something else.

Ubuntu will still print the motd regardless of the configuration in /etc/ssh/sshd_config because of pam.

To disable it, 

```
sudo vim /etc/pam.d/sshd
```

and put a hash in front of the line with pam_motd.so

```

# Print the message of the day upon successful login.
#session    optional     pam_motd.so # [1]

```

---


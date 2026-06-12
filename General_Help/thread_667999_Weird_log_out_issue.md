---
title: "Weird log out issue"
date: 2008-01-14
forum: General Help
---

### Post by Hawk__0 on 2008-01-14
So today, I'm just using my computer as I normally would, and I get logged out.  I'm just like wtf!?
Anyhow, if i tried to log back in, I was not able to.

Then it happened again, but this time i was able to log back in without restarting.

This also happened once yesterday.

I have ssh x11 forwarding enabled.. could this be my problem? and that someone is trying to breach my system? here is my ssh config:

```
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes



```
the uselogin, i have a feeling, means they dont have to log in with a password if they use X.  am i right?

whether that is the problem or not, im confused.  anyone ever had this problem before?

---

### Post by tgalati4 on 2008-01-15
Check your /var/log and see what entries you have.  Remote sessions will leave droppings.

---


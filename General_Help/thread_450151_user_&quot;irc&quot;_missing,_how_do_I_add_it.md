---
title: "user &quot;irc&quot; missing, how do I add it?"
date: 2007-05-21
forum: General Help
---

### Post by kvonb on 2007-05-21
When I install any IRCd prog through Synaptic, I always get an error at the end which won't go away:

```
Setting up ircd-hybrid (7.0.3-3.1) ...
chown: `irc:irc': invalid user
dpkg: error processing ircd-hybrid (--configure):
subprocess post-installation script returned error exit status 1

```

It comes from the post installation script which is trying to do some work with user "irc", however that user does not exist.

This is the offending line from postinst:

```
chown irc:irc /var/run/ircd /var/log/ircd /etc/ircd-hybrid
chmod 770 /etc/ircd-hybrid
```

So my question is: how do I create a system user irc, ie a non-password user?

---

### Post by kvonb on 2007-05-21
OK, I found out how to add a system user for anyone who is interested:

```
sudo adduser --system --group --no-create-home irc
```

---


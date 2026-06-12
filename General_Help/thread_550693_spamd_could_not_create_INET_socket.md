---
title: "spamd: could not create INET socket"
date: 2007-09-14
forum: General Help
---

### Post by kiffles on 2007-09-14
Hi all, 

I'm new to Ubuntu and currently scratching my head with this error message. 

I've followed the instructions to setup Spamassassin and it seems to be working and catching the spam. I made a change to the configuration and went to restart spamassassin using:

# sudo /etc/init.d/spamassassin restart

But got this message:

```
Restarting SpamAssassin Mail Filter Daemon: No spamd found running; none killed.
error: spamd: could not create INET socket on 127.0.0.1:783: Address already in use
spamd: could not create INET socket on 127.0.0.1:783: Address already in use
```

It's not restarting because I've changed the required score from 5.0 to 2.0 but it's still displaying 5.0 in the spam email headers.

To see what was running on port 783 I've run:
# netstat -luntp | grep 783

With the result
```
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN     26340/spamd --creat
```

I've searched on forums and Google but cant seem to find a solution on what to do to get this to work :confused:

---

### Post by boltymac on 2007-12-13
Hi,

Did you ever manage to resolve this issue.  I am having the same problem.

Thanks

---

### Post by kiffles on 2007-12-13
> **boltymac said:**
> Hi,

Did you ever manage to resolve this issue.  I am having the same problem.

Thanks

Hi boltymac,

I restarted my whole server and everything started working correctly.

---


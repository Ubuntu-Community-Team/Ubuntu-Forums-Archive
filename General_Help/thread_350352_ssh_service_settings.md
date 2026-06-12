---
title: "ssh service settings?"
date: 2007-01-31
forum: General Help
---

### Post by giants_fan on 2007-01-31
Hi,

Why doesn't SSHD show up in the list of services when you do System->Administration->Services?

I know SSH is running, but is there a way to turn it on/off graphically?

Thanks!

---

### Post by heathenx on 2007-01-31
install bum (boot-up manager). that should allow you to see sshd service graphically and allow for you to turn it off and on.

of course you can always use the terminal:

sudo ps -e (to see services)

sudo /etc/init.d/sshd stop
sudo /etc/init.d/sshd start

---


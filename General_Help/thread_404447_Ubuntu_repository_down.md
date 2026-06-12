---
title: "Ubuntu repository down?"
date: 2007-04-08
forum: General Help
---

### Post by statue on 2007-04-08
Is anyone else having this problem: I can't seem to download anything from us.archive.ubuntu.com - the progress just stops whenever it has to connect to that site and it seems to have to go there for just about every package - Is there a different site I could use? Thanks


EDIT: Turns out my firewall was restricting it...it's working now. Thanks for the reply, bruenig

---

### Post by bruenig on 2007-04-08
> **statue said:**
> Is anyone else having this problem: I can't seem to download anything from us.archive.ubuntu.com - the progress just stops whenever it has to connect to that site and it seems to have to go there for just about every package - Is there a different site I could use? Thanks

It is working for me, if you want, you can change the mirror.
```
sudo sed 's/\/us./\/ca./g' -i.backup /etc/apt/sources.list && sudo apt-get update
``` will change it to canadian mirrors.

---

### Post by corefile on 2007-04-19
> **statue said:**
> Is anyone else having this problem: I can't seem to download anything from us.archive.ubuntu.com - the progress just stops whenever it has to connect to that site and it seems to have to go there for just about every package - Is there a different site I could use? Thanks


EDIT: Turns out my firewall was restricting it...it's working now. Thanks for the reply, bruenig

how was your firewall blocking just that repository?

---

### Post by wh0rd on 2007-04-20
CA repos are also having some issues. I'm on the UK repo, it's working lightening fast.

---


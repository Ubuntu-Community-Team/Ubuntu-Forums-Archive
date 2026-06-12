---
title: "Ubuntu One message on log on"
date: 2014-07-09
forum: General Help
---

### Post by richpri on 2014-07-09
Some time in May a message started to appear in the upper right corner of my screen every time I logged on to Ubuntu.
The message was about the termination of Ubuntu One.

I am still getting the message way after the termination date! How can I get rid of it?

---

### Post by grier-devon on 2014-07-09
Is Ubuntu One still installed? If so I would uninstall Ubuntu One through the software center, not like you can use it anymore anyway.

---

### Post by slickymaster on 2014-07-09
> **richpri said:**
> Some time in May a message started to appear in the upper right corner of my screen every time I logged on to Ubuntu.
The message was about the termination of Ubuntu One.

I am still getting the message way after the termination date! How can I get rid of it?

You need to remove the **python-ubuntuone-storageprotocol** package. You can do this via the Software Center or via the command line:```
sudo apt-get autoremove --purge python-ubuntuone-storageprotocol
```

---

### Post by NM5TF on 2014-07-09
thanx for that Slickymaster...I also was having that same message appear...

tommy

---


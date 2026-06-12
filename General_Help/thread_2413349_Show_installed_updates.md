---
title: "Show installed updates"
date: 2019-02-24
forum: General Help
---

### Post by cam17 on 2019-02-24
How can I view the currently installed updates on 18.04?

---

### Post by ajgreeny on 2019-02-24
You can run command ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list all packages that have been upgraded by date.

You can even go further back in time by using zgrep on the archived dpkg.log.2.gz etc etc, with command ```
zgrep -i " upgrade " /var/log/dpkg.log.*
``` though that output will be huge and probably less useful to you.

---

### Post by cam17 on 2019-02-25
That update sounds like it is time dependent. I am looking for all updates performed since the first update request.

Will that provide me with all updates?

---

### Post by ajgreeny on 2019-02-26
I am not sure how many of those numbered **dpkg.log.#.gz** are retained nor for how long but on my system the oldest of them **dpkg.log.12.gz**goes back well over 12 months.

---

### Post by #&amp;thj^% on 2019-02-26
It has always been my understanding since 16.04/xenial and newer, /var/log/apt contains a history of package installations. However, by default, it is managed by logrotate which compresses and ages out old entries.

---

### Post by deadflowr on 2019-02-26
> How can I view the currently installed updates on 18.04?
You can run
```
apt list | grep updates
```
that would list all packages that have been updated.

If you want to know when or how often anything has been updated you'd be best to read the log files directed to already.

You used to be able to view history in the old software center but that is no longer in the repos.

Not sure if any other gui has an option quite like that.
I know synaptic has a history option but I thought that was related to synaptic actions.
(and not apt history as a whole)

---

### Post by cam17 on 2019-03-07
Thanks that answers my question

---


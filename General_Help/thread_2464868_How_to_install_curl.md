---
title: "How to install curl"
date: 2021-07-14
forum: General Help
---

### Post by satimis on 2021-07-14
Hi all,

Please advise how to install curl

$ sudo install curl```

install: missing destination file operand after 'curl'

```

Thanks in advance

Regards

---

### Post by satimis on 2021-07-14
Hi all,

Problem solved.  I have to run;
$ sudo apt update
first.

Now;
$ which curl```

/usr/bin/curl

```

Regards

---

### Post by TheFu on 2021-07-15
> **satimis said:**
> Hi all,

Please advise how to install curl

$ sudo install curl```

install: missing destination file operand after 'curl'

```

Well, that's the wrong command.
```
sudo apt install curl
``` would work.  You are hardly the first person to do that, today, this hour. We all do it.  The error was complicated because "install" is a valid program, but it has nothing to do with APT, so you got install saying "you asked me to do something I don't know who to do."

The *apt update* wasn't likely needed, other than it got you to type "apt"

---

### Post by satimis on 2021-07-15
> **TheFu said:**
> Well, that's the wrong command.
```
sudo apt install curl
``` would work.  You are hardly the first person to do that, today, this hour. We all do it.  The error was complicated because "install" is a valid program, but it has nothing to do with APT, so you got install saying "you asked me to do something I don't know who to do."

The *apt update* wasn't likely needed, other than it got you to type "apt"
Sorry that was my typing mistake leaving out "apt"

Actually I ran "sudo apt install curl"

Regards

---

### Post by TheFu on 2021-07-15
> **satimis said:**
> Sorry that was my typing mistake leaving out "apt"

Actually I ran "sudo apt install curl"

Well, my testing here shows this:
```
$ install curl
[COLOR="#FF0000"]install: missing destination file operand after 'curl'[/COLOR]
Try 'install --help' for more information.
```
which maps exactly to the result shown above.  I still think you left off the "apt" in the original command.  It is common.  I've done it and expect to keep doing it about once a month the rest of my life.

---


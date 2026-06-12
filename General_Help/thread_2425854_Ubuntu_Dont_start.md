---
title: "Ubuntu Dont start"
date: 2019-08-31
forum: General Help
---

### Post by waffen on 2019-08-31
Hello,

Today I was working in my PC, I need to restart it and Ubuntu cant do that and a black screen appears please check the attached image, What can I do?

Im using Ubuntu 16.04 LTS uptodate.

Thanks in advance!

[ATTACH=CONFIG]283903[/ATTACH]

---

### Post by Bashing-om on 2019-08-31
waffen; Hello -

Do as the kernel suggest "manual fsck" :)

Boot up a liveUSB/DVD in "try ubuntu" mode, activate a terminal -
In this terminal run:
```

sudo fsck /dev/sda1

```
Reboot into the install and -
Advise of the result.

[INDENT][INDENT]maybe all good now
[/INDENT][/INDENT]

---

### Post by waffen on 2019-08-31
Oh thanks! I'm out of my home right now, I'll post the result later.

---


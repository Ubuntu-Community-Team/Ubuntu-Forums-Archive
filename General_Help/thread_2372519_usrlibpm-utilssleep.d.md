---
title: "/usr/lib/pm-utils/sleep.d"
date: 2017-09-26
forum: General Help
---

### Post by ulrichmuc on 2017-09-26
I put a script 01test  

> #!/bin/sh
echo `date` $1 >> /tmp/resume

into  /usr/lib/pm-utils/sleep.d and expected to see a result in /tmp/resume after a suspend/resume cycle.
But noting happens.

Any explanation?

---

### Post by &amp;KyT$0P# on 2017-09-26
What version of Ubuntu are you using?

---

### Post by ulrichmuc on 2017-09-26
I am using ubuntu    16.04.3 LTS with Mate desktop

---

### Post by &amp;KyT$0P# on 2017-09-26
> **ulrichmuc said:**
> I am using ubuntu    16.04.3 LTS 
16.04 doesn't use the sleep.d folders.  You need to set up a systemd service for your script.

Create a file [FONT=Courier New]/etc/systemd/system/sleep-test.service[/FONT] and fill it with this -
```
[Unit]
Description=Whatever description you want
Before=sleep.target
StopWhenUnneeded=yes

[Service]
Type=simple
RemainAfterExit=yes
ExecStart=-/full/path/to/your/script suspend
ExecStop=-/full/path/to/your/script resume

[Install]
WantedBy=sleep.target
```
Replace the Description and [FONT=Courier New]/full/path/to/your/script[/FONT].  Then enable your service -
```
sudo systemctl enable sleep-test
```

Does it work now?

Refer to [FONT=Courier New]man systemd.service[/FONT] and [FONT=Courier New]man systemd.unit[/FONT] for more info

---

### Post by ulrichmuc on 2017-09-27
Yes, this works fine. Thanks a lot.

Two questions:

Does this affect any other actions needed by suspend/resume?

Why is the directory /usr/lib/pm-utils/sleep.d still there, and filled? Confusing!

Kind regards,

ulrich

---


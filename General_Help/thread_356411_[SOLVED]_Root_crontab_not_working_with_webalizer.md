---
title: "[SOLVED] Root crontab not working with webalizer"
date: 2007-02-08
forum: General Help
---

### Post by chrismyers on 2007-02-08
Hi there.

Does anyone know how I can work out why my crontab doesnt work:

# m h  dom mon dow   command
10 * * * * /usr/bin/webalizer

This should run every 10 minutes, but it doesn't.

However, just manually running /usr/bin/webalizer works fine.

What am I doing wrong? are there any logs I can check to find a solution?

Cheers.

---

### Post by Stu09 on 2007-02-13
I'm having a similar problem with crontab.
Anyone have a solution ?

---

### Post by llamakc on 2007-02-13
# m h  dom mon dow   command
10 * * * * /usr/bin/webalizer -c /etc/webalizer.conf

---

### Post by chrismyers on 2007-02-15
Thank you very much. That worked like a charm.

:lolflag:

---


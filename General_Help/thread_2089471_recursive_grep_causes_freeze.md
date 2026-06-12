---
title: "recursive grep causes freeze"
date: 2012-11-29
forum: General Help
---

### Post by ikt on 2012-11-29
Hi there,

I have a headless debian 6 box, and when I run:

grep -re "file" / 

It'll show it going through a whole heap of devices and then the output stops and the server stops responding to everything.

Has anyone seen this before?

---

### Post by Habitual on 2012-11-29
don't grep the / directory?

---

### Post by ikt on 2012-11-29
> **Habitual said:**
> don't grep the / directory?

Yeah, I try not to, I've done it now twice by accident.

The thing is that it greps the root directory fine right now, so something is causing it to fail long after it's been up, would be interested to find out if anyone has a similar story.

---


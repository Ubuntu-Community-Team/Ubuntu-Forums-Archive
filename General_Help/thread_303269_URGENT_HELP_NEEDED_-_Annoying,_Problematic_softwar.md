---
title: "URGENT HELP NEEDED - Annoying, Problematic software stops box from shutting down"
date: 2006-11-20
forum: General Help
---

### Post by Portable_Jim on 2006-11-20
This thread is solved

HELP NEEDED _**URGENTLY!!!**_ (so ugently I am wiriting this on another computer)

_**[SIZE=5]Major concern:[/SIZE]**_ [SIZE=5]does anyone know how to uninstall software from the command line (synaptic froze when trying to uninstall it).[/SIZE]

Concern #2:Every time I shutdown the following meddage comaes up:
[code][ [SIZE=1]*(numbers of increacing value)*[SIZE=3]] unregister_netdevice: waiting for vmnet1 to become free. Usage count = 1[/SIZE][/SIZE][/quote]

---

### Post by Portable_Jim on 2006-11-20
I fixed my own problem:

I restarted, then chose recovery mode. When prompted I gave the root pasword and pressed enter. I then ran ```
aptitude
``` and uninstalled the problem program.

Note: aptitude is not half bad.

---

### Post by Portable_Jim on 2006-11-20
Could a moderater please close the thread - it is finished. I found my own answer.

---

### Post by DigitalAxis on 2006-11-20
You might also want to change the thread title to "[SOLVED] -Annoying, Problematic software stops box from shutting down" (or somesuch)

And I agree- aptitude is great.  The reverse dependency handling alone makes it better than apt-get (and therefore synaptic) in my eyes.

---

### Post by yopnono on 2006-11-20
Other thing.... Please don't use panic topics and large text like in this post.

Better use some less panic topic.

Good to hear that you fixed it.

---


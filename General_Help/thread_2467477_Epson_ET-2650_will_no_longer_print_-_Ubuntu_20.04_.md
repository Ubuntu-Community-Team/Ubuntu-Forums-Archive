---
title: "Epson ET-2650 will no longer print - Ubuntu 20.04 LTS"
date: 2021-09-28
forum: General Help
---

### Post by John Nagle on 2021-09-28
AARGH! Content lost due to "security token missing". Actual content follows.

---

### Post by John Nagle on 2021-09-28
Printer used to work, but is no longer working.
Local Epson ET-2650 on USB.

Error message is " 'No suitable destination host ''found by cups-browsed.'

Other messages include "Scheduler not running".

Ubuntu 20.04 LTS, updated today. Failed both before and after update.

I tried running "sudo cups-browsed --debug", and was able to get a test page printed once. So the printer is alive and well. But I can't print files. The printer goes from "Active" to Not active.

Tried the "troubleshooter". No good. Some of the output is attached.

Ubuntu docs indicate that "cups-browsed" is "deprecated". So why am I getting messages about it not running?

---

### Post by QIII on 2021-09-28
There is a character limit which, when exceeded, causes that error.

Please try to break things up into smaller chunks, or, if posting long results from terminal commands, consider using something like [Ubuntu Pastebin]("https://pastebin.ubuntu.com/") and leaving a link.

---


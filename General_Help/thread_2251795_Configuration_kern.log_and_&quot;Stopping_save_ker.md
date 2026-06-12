---
title: "Configuration: kern.log and &quot;Stopping save kernel messages&quot;"
date: 2014-11-06
forum: General Help
---

### Post by stimits on 2014-11-06
I'm using an ARMv7 Ubuntu 14.04 LTS and trying to develop kernel modules. Unfortunately I don't know enough about Ubuntu configuration, and a recent update to rsyslog resulted in kern.log no longer updating (not very good if debugging modules via printk). To see any messages I now must tail dmesg (no files contain kernel logs anymore). I compared configurations that I know of for rsyslog between the latest update and what I had backed up from a few months ago, and see very little change...certainly nothing which would cause logs to stop. I'm trying to figure out how to re-enable kernel logging.

It's worth noting that at times the ARMv7 version is a few months behind updates to x86 packages. So this "recent" update may have occurred a while back to x86.

Just today I noticed a message I've not seen before during boot:
**[FONT=courier new]Stopping save kernel messages[/FONT]**

The only web search I've found on this was that around July x86 distributions sometimes had a failure to boot past this, but it was only coincidental that this message was pasted into the failed boot reports. This system does not fail to boot, but it seems likely the message is related to kern.log no longer functioning. Perhaps it is a concept that embedded or smaller systems shouldn't save logs, but I need these logs for my work (it's very annoying to always dmesg and tail rather than tail -f on kern.log). What configuration or software causes this "Stopping save kernel messages" to appear? Is this what causes an intentional non-bug stop of logging of kernel messages? Or is kern.log failure a bug? If not a bug, what configuration do I change to get my logs to start functioning again?

---


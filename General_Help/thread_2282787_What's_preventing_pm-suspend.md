---
title: "What's preventing pm-suspend?"
date: 2015-06-16
forum: General Help
---

### Post by fbugnon on 2015-06-16
I have a ThinkPad X1 Carbon running 14.04 Ubuntu.

_Short-version_:  sometimes my computer will not sleep and I need to know what's preventing it from.

Few days ago I notice that the laptop was running although the lid was closed.  Since then, it happens quite often, usually after a day of working (it never happens right after a fresh reboot). When the problem occurs, using the command "sudo pm-suspend" or pressing Fn+F4 has the same effect:  the sleep led lights up for a short time, but it's like something wakes the computer up after a second or so...  and I can't find out what it is.

No error or failure messages I could find. I've search a bit and I've tried to look at /var/logs/pm-suspend.log but nothing that I could notice. ;)

So, my question is, how can I find out what's preventing my computer from sleeping?

Any ideas would be appreciated. Thanks!

---

### Post by fbugnon on 2015-06-17
Searching a bit further, on AskUbuntu I found reference to a [solution]("http://ubuntuforums.org/showthread.php?t=1978290&p=12014988#post12014988") in ubuntuforums, which apparently is working for me!

(see post #6 on the link above)

---


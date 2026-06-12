---
title: "Weird: lightdm doesn't start until I switch to tty2"
date: 2018-12-01
forum: General Help
---

### Post by yetanotheruser on 2018-12-01
Hi everyone, I'm a long time, if basic, Ubuntu user but this is new to me and I couldn't find anything similar posted elsewhere.
Since I upgraded to Ubuntu 18.10 on my Dell Inspiron 3552, when booting it hangs on "Starting GNOME Display".
It stays there indefinitely, unless I switch to tty2, then back to tty1.
At that point, lightdm loads after a few seconds.

Its not that bad of a problem, but I'm wondering what it might be due to...
I'm also not sure which logs to attach:
dmesg has nothing that seems relevant, /var/log/lightdm/*.log are all empty, and /var/log/Xorg.0.log shows it starting without error at second 300 (when I do the switch tty thing)

Any clues? :confused:

Much appreciated!
Thanks

---


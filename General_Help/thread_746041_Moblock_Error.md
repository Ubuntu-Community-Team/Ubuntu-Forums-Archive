---
title: "Moblock Error"
date: 2008-04-05
forum: General Help
---

### Post by Stabilityonitsown on 2008-04-05
Hi guys just want to say that I am using Debian!

Anyways MoBlock has been acting up ever since I got it, errors here, errors there, I have to fight it just to browse the web. But basically the error I am getting is

Error 6: The setting IPTABLES_ACTIVATION=2 in /etc/moblock/moblock.conf
is no more valid.

It is super annoying. And another thing it always crashes when it starts, I don't know if its because the error or something else but the only time when it is actually running is when its updating or reloading or restarting. I am using mobloquer and I am also having issues with that too. See everytime it starts everything looks like a little kid got a marker and went to town,just a scribble mess!!!

Please help me fix this guys, I beg you, I offer thanks in return, lots and lots of thanks to all contributers, because I cannot surf the web or download without blocklists.

---

### Post by jre on 2008-04-05
Make sure that in /etc/moblock/moblock.conf IPTABLES_ACTIVATION=**"1"** is set.
Do the same in /etc/default/moblock or just delete that line there.

If moblock-control outputs an error (as it did in your case) it exits. So with your current configuration MoBlock will never be started.

Finally (but not that important) I guess that your packages are outdated - so make an update.

---


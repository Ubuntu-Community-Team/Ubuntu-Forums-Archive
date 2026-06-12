---
title: "How to disable firestarter in boot time?"
date: 2006-12-07
forum: General Help
---

### Post by Prism on 2006-12-07
Hi there,

I'd like to use firestarter as my firewall. Problem is, when I boot into Ubuntu a message box keeps popping saying "insufficient privileged" etc.

I've searched the forum and seen there isn't any way to stop the message from popping having firestarter running, so basically I'd like not to have firestarter running :)

I tried to remove firestarter from my boot sequence using sysv-rc-conf, but it didn't help. [FONT="Courier New"]/etc/init.d/firestarter status[/FONT] reports "firestarter is stopped", but that message is still popping up.

Anything else I can do? I've heard edgy has a new boot system. Maybe that's the reason sysv-rc-conf didn't help?

Thanks in advance. :)

---

### Post by Prism on 2006-12-07
Never mind. I use shorewall instead. It seems like a more powerful firewall, but it takes long time to configure it.

---


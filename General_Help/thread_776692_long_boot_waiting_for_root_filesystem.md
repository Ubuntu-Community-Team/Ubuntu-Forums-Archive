---
title: "long boot: waiting for root filesystem"
date: 2008-04-30
forum: General Help
---

### Post by agim on 2008-04-30
I have had a great Hardy experience so far. My sole complaint is that it takes about 20 seconds longer to boot on my machine than 7.10, and I would like to get it back under a minute.

I have two questions:

1) After removing the 'quiet' from my menu.lst, I saw that it took about 10 seconds on boot for "reading files needed to boot". And while this is happening, the loading bar graphic stops, and inches its way along, which it never did on any previous version... So the question is, what can I do about it.

2) Is there any way to save all of those messages streaming through on boot-up to a file?

Thanks

---

### Post by agim on 2008-05-01
bump

---

### Post by cilynx on 2008-08-21
"All those messages" tend to wind up in /var/log/messages and/or /var/log/syslog.  You can also get everything by typing 'dmesg' on a command line.

---


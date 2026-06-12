---
title: "Unable to find message on boot before Ubuntu loading screen"
date: 2006-09-06
forum: General Help
---

### Post by Coomkeen on 2006-09-06
Hi,

I get an 'Unable to find....' message after selecting Ubuntu in Grub, and a few milliseconds before the Ubuntu loading screen comes up.
It's far to quick to read more than that.
Is there any way of reading these messages before they dissappear, or maybe they are logged in a file somewhere?

It doesn't seem to affect Ubuntu, or at least I haven't found anything missing.

I'm a bit of a newbie at Linux, so simple explanations please :confused:

---

### Post by taurus on 2006-09-06
You can view it in /var/log/messages or with the dmesg command...

```

sudo more /var/log/message (hit space bar for the next 24 lines of text...)
dmesg | more (hit space bar for the next 24 lines of text...)

```

---

### Post by Coomkeen on 2006-09-06
Thanks.
Loads of messages - I'll keep looking now I know where.
thanks again.

---

### Post by ayoli on 2006-09-06
there's also the graphical way using gnome log viewer which is in menu System > Administration.
when launched hit ctrl+F to be able to filter/search

---


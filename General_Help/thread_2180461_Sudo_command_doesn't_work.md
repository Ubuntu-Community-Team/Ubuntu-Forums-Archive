---
title: "Sudo command doesn't work"
date: 2013-10-13
forum: General Help
---

### Post by Viktor_Hundahl_Strate on 2013-10-13
Hi, when i try to use the sudo command it says
[B]
/etc/sudoers: syntax error close to line 19
interpretation errors in /etc/sudoers close to line 19
no vaild sudoersource found, ending
can not initialize extension module for policy

[/B]translated from my langue to english
can i get access to the /etc/sudoers file without the sudo command

Please Help! :)

---

### Post by Lars Noodén on 2013-10-13
It's fixable, you just need to boot to recovery mode.  In practice, you need to **always** test the correctness of /etc/sudoers when editing it **before** closing it.  One common way to do that is to edit it with [visudo](http://manpages.ubuntu.com/manpages/raring/en/man8/visudo.8.html)

Now that you're in a hard spot, about your only option is to reboot into recovery mode and then fix /etc/sudoers  If you haven't changed Grub then you can go in that way.  Otherwise, you may have to use a Live DVD or CD.

---

### Post by oldos2er on 2013-10-13
There's a default copy of /etc/sudoers here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by sisco311 on 2013-10-13
Assuming that your user is in the admin or sudo group, you don't have to boot into recovery mode. You can use pkexec to run a command as another user:```
pkexec visudo
```

---


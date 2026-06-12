---
title: "Removed self from sudoers file with usermod command [Resolved]"
date: 2006-11-10
forum: General Help
---

### Post by veraction on 2006-11-10
When setting up subversion, I accidently removed myself from the sudoers file (because of a howto...):

```

[COLOR="Red"]# don't do this -- it'll screw you[/COLOR]
$ sudo usermod -Gsubversion myusername

```

How can I have a functioning system again? I don't have any other users with sudo privileges to add me back.

---

### Post by taurus on 2006-11-10
Boot into recovery mode from GRUB and edit it with visudo or add yourself back into groups adm & admin in /etc/group...

---

### Post by veraction on 2006-11-10
I think I found the solution - 

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

I'll post my results

---

### Post by veraction on 2006-11-10
Ah, thank god for recovery mode.

Just booted up into that, then ran ```
addgroup myusername admin
```

issue resolved

---


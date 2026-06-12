---
title: "sudo: unable to resolve host XXX"
date: 2015-01-03
forum: General Help
---

### Post by ofnuts on 2015-01-03
Just installed 14.04. Everything seems to work fine, but when I use sudo, I get a:
```

sudo: unable to resolve host XXX

```

where XXX is the host name (as also returned by 'hostname'). The sudo command itself then proceeds normally, so it just  minor annoyance, unless it's the symptom of something that is going to hit me later? And why is sudo trying to resolve the host name anyway?

---

### Post by nerdtron on 2015-01-03
how about the contents of the /etc/hosts file?

---

### Post by sudodus on 2015-01-03
Did it occur after using chroot?

*Edit*: I have no such problem in an up to date installed system of Lubuntu 14.04.1 LTS (32-bit), but I know it can appear after chrooting.

---

### Post by ofnuts on 2015-01-03
Good question :) I happen to have overwirtten the post-install "hosts" with the one I used on the previous instance of the system, where the  machine assumed another name. So everything is fine now. I still don't know why sudo needs to resolve the hosts name, though.

---


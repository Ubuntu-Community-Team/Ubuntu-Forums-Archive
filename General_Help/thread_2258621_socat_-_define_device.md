---
title: "socat - define device"
date: 2014-12-29
forum: General Help
---

### Post by eslavko on 2014-12-29
Hello...
I need serial loopback device and I use socat to create it.
```
socat -d -d pty,raw,echo=0 pty,raw,echo=0
```

It works but I wish to be able to set device name.
Ie when I start I usaly got /dev/pts/23 and /dev/pts/24 but sometime I got /dev/pts/11 and /dev/pts/24.
Is there a way to set permanent pts ports (/dev/pts/98 and /dev/pts/99 for example?)

Thanks

---

### Post by schragge on 2014-12-29
From the [socat(1)](http://manpages.ubuntu.com/manpages/trusty/en/man1/socat.1.html) manpage:
> **link=<filename>**
Generates a symbolic link that points to the actual pseudo terminal (pty). This might help to solve the problem that ptys are generated with more or less unpredictable names, making  it difficult to directly access the socat generated pty automatically. With this option, the user can specify  a  "fix" point  in the file hierarchy that helps him to access the actual pty (example).  Beginning with **socat** version 1.4.3, the symbolic link is removed  when the address is closed (but see option unlink-close).

---

### Post by eslavko on 2014-12-29
Hello...
I can't figure out how to create two pts's and linked with link...
Can someone provide commandline?

Thanks

---

### Post by schragge on 2014-12-29
Does this work for you?
```
socat -d -d pty,raw,echo=0,link=/tmp/ttyV0 pty,raw,echo=0,link=/tmp/ttyV1
```

---

### Post by eslavko on 2014-12-29
> **schragge said:**
> Does this work for you?
```
socat -d -d pty,raw,echo=0,link=/tmp/ttyV0 pty,raw,echo=0,link=/tmp/ttyV1
```

Yes... 
That's work. Now if I understand correctly socat opens two /dev/pts/ (with number not constant) but linked to constant /tmp/ttyVx...

Thanks.

---


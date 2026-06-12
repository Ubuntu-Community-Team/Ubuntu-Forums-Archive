---
title: "how to get xinetd to launch deluge-web"
date: 2013-01-28
forum: General Help
---

### Post by bvargo on 2013-01-28
I installed proftpd under xinetd and it appears to be working...I figured it would make sense to launch deluge-web under xinetd since i don't really use it much.

```

/etc/xinetd.d$ cat deluge-web
service deluge-web
{
flags = REUSE
socket_type = stream
protocol = tcp
wait = no
user = deluge
server = /usr/bin/deluge-web
instances = 20
port = 8112
}

```


I have the file path right:
```

/etc/xinetd.d$ ll /usr/bin/deluge-web
-rwxr-xr-x 1 root root 304 Oct 12 01:14 /usr/bin/deluge-web*

```

The port is right ( I copied and pasted it).

```

/etc/xinetd.d$ sudo groups deluge
deluge : library

```


Is this not something that can be launched from xinetd or is something else wrong?

---


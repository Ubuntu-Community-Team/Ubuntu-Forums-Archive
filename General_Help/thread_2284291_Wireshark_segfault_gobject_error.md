---
title: "Wireshark segfault gobject error"
date: 2015-06-28
forum: General Help
---

### Post by monkeybrain20122 on 2015-06-28
Hi, since a few days ago wireshark segfaults whenever it starts (it worked before) 

dmesg produced 

```
wireshark[2320]: segfault at ffffffffa4004920 ip 00007fa5bc13d425 sp 00007ffcb149fbb8 error 5 in libgobject-2.0.so.0.4400.1[7fa5bc10a000+50000]

```

libglib2-2.0 was updated a few days ago. I think this is the culprit.

```
Upgraded the following packages:
libglib2.0-0 (2.44.0-1ubuntu3) to 2.44.1-1ubuntu1
libglib2.0-0:i386 (2.44.0-1ubuntu3) to 2.44.1-1ubuntu1
libglib2.0-bin (2.44.0-1ubuntu3) to 2.44.1-1ubuntu1
libglib2.0-data (2.44.0-1ubuntu3) to 2.44.1-1ubuntu1
libglib2.0-dev (2.44.0-1ubuntu3) to 2.44.1-1ubuntu1

```

I have recompiled wireshark but problem persists. If there is no other way to fix it, version  of 2.44.01ubuntu3 of these packages are still in the repo, but trying to downgrade one would remove a long list of things. I am wondering if there is a way to downgrade all of them simultaneously.

Ubuntu 15.04 64 bit.

Thanks.

---

### Post by monkeybrain20122 on 2015-06-29
However it starts without segfaulting with sudo. there is a warning
> Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged

So GtkDialog mapped with a transit parent (whatever that means) might be the problem?

---

### Post by monkeybrain20122 on 2015-06-30
Installed wireshark 1.2.16 from ppa and the problem goes away. [https://launchpad.net/~wireshark-dev/+archive/ubuntu/stable](https://launchpad.net/~wireshark-dev/+archive/ubuntu/stable) Not sure why my build started seggfaulting after the libglib update (I have recompiled several times afterwards with no avail), but I am marking this as solved.

---


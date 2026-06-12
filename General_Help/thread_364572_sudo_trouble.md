---
title: "sudo trouble"
date: 2007-02-18
forum: General Help
---

### Post by drewu on 2007-02-18
I was messing around with my ubuntu box trying to get networking to work and I may have broken my sudo command! Every time I use it for anything now, I get this error:

```
sudo: unable to lookup T411c2 via gethostname()
```

And nothing else.

Any ideas how I managed this?
Thanks.

---

### Post by taurus on 2007-02-18
Boot into recovery mode post these two files here.

```
cat   /etc/hostname
cat   /etc/hosts
```

---

### Post by drewu on 2007-02-18
cat   /etc/hostname:
```
T411c2
```

cat   /etc/hosts:
```

# The following lines are desirable for IOv6 capable hosts
```

Not much, is it?

---

### Post by taurus on 2007-02-18
Nothing in /etc/hosts!  That's why sudo all screws up and I bet your network is screwed too.

While still in the recovery mode, edit /etc/hosts

```
nano /etc/hosts
```
and add these lines to it.

```

127.0.0.1       localhost
127.0.1.1       T411c2

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Save it and exit with <Ctrl>x.  Then Y and Return.  Reboot and see if you can use sudo again.

```
shutdown -r now
```

---

### Post by Maestro23 on 2007-02-18
Taurus, I was too slow. Getting ready to post that myself after looking at mine.:)

---

### Post by drewu on 2007-02-18
You guys are the best. Thanks a bunch!

---


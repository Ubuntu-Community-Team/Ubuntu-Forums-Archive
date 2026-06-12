---
title: "Disappearing ttys with sysvinit (Feisty)"
date: 2007-06-25
forum: General Help
---

### Post by quark_77 on 2007-06-25
Hi All,

In my quest to experiment with SELinux on Ubuntu I've had to unpick a few things, one of them being upstart [1]. I'm now running sysvinit in it's place (/etc/event.d is intact) and have recently noticed my ttys have disappeared. I switch to them using Ctrl+Alt+F2 and I can see a flashing _ cursor but no login prompt...

 Here's the relavent code from /etc/inittab...
```
1:2345:respawn:/sbin/getty 38400 tty1
2:2345:respawn:/sbin/getty 38400 tty2
3:2345:respawn:/sbin/getty 38400 tty3
4:2345:respawn:/sbin/getty 38400 tty4
5:2345:respawn:/sbin/getty 38400 tty5
6:2345:respawn:/sbin/getty 38400 tty6

```
Now, if I log in (via X) I can do the following:
```
sudo getty 38400 tty8
```
Which not only pokes the other ttys into action but creates tty8 as it should. My question is, how do I get my ttys back automatically?

Due to the fact I'm running LUKS encrypted partitions my kernel options are simply:
> ro enforcing=0
So no quiet and no usplash otherwise I can't see the 'Enter LUKS passphrase' bit or even remotely guess whether it's there.

In case it's important I'm also running kernel 2.6.21.3 custom compiled and was working with ttys until I replaced upstart. Also a problem on generic Feisty kernel.

Any help would be much appreciated!!

Quark_77

[1]: Upstart doesn't automatically load SELinux policies as yet... until it does I have to use sysvinit.

---


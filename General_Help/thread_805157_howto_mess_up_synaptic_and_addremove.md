---
title: "howto mess up synaptic and add/remove"
date: 2008-05-23
forum: General Help
---

### Post by bamboomy on 2008-05-23
Hi,

I ran into a problem with my new hardy and solved it but couldn't resist to share my experience into a useless how-not-to :D

The thing you'll be learning here has absolutely no practical use (I guess) but it's kinda fun and linux is all about fun, right ?

OK, what we are going to do is mess up synaptic, add/remove and even the update manager without touching the command line apt way of installing new software.

The thing we are going to attack is the graphical sudo, well, we're going to attack sudo all together but the command line interface just gives a warning and the graphical one freezes.

The only thing you need to do is to replace the string in /etc/hostname with some line that's not included in /etc/hosts

My sample /etc/hostname looks like this:
```

castle

```

and my /etc/hosts like this:
```

127.0.0.1	localhost
127.0.1.1	castle

```

If we change /etc/hostname to:
```

example

```

and reboot the sudo command will print out something like 'could not find hostname example' and we are set:
-> trying to install something graphically will call sudo and sudo will give the warning and never comes to actually asking the sudo password. The application just freezes and it seems like you can't install software anymore. The way of reversing the damage is of course either putting 'example' in /etc/hosts or setting back the old value in /etc/hostname, the latter needs a reboot.

Sofar my little how-not-to :D

grtz,

S.

---

### Post by K.Mandla on 2008-05-29
Moved to General Help.

---


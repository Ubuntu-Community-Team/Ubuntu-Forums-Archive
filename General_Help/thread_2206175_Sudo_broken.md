---
title: "Sudo broken"
date: 2014-02-17
forum: General Help
---

### Post by oozaru on 2014-02-17
when I try to use sudo in the command line I get this:

```
sudo: /etc/sudoers is owned by uid 444, should be 0
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

```

---

### Post by Frogs Hair on 2014-02-17
Possibly related . 

[http://askubuntu.com/questions/170216/sudo-doesnt-work](http://askubuntu.com/questions/170216/sudo-doesnt-work)

[http://askubuntu.com/questions/209558/how-can-i-fix-broken-sudo-sudo-parse-error-in-etc-sudoers-near-line-23](http://askubuntu.com/questions/209558/how-can-i-fix-broken-sudo-sudo-parse-error-in-etc-sudoers-near-line-23)

---

### Post by deadflowr on 2014-02-17
Somehow an issue like this came up just yesterday, somewhere I posted, and this link was provided by someone else.
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by jeanjd63 on 2014-02-18
> **oozaru said:**
> when I try to use sudo in the command line I get this:

```
sudo: /etc/sudoers is owned by uid 444, should be 0
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

```


What have you done on directory /etc ?
Have you change something like chown ......

---

### Post by fdrake on 2014-02-18
@deadflowr 
i don't think that will help. it looks like the OP issue is an ownership (and file corruption) not permission.

@OP 
it looks like your sudo file is not valid or corrupted . try to reinstall it with a live-cd , chroot your partition as root  user ([https://wiki.sabayon.org/index.php?title=HOWTO:_chroot_from_a_LiveCD](https://wiki.sabayon.org/index.php?title=HOWTO:_chroot_from_a_LiveCD)) and run
```
apt-get --reinstall install sudo
```

if you don't have a live cd try to boot into single mode and try the prev command ([http://askubuntu.com/questions/132965/how-do-i-boot-into-single-user-mode-from-grub](http://askubuntu.com/questions/132965/how-do-i-boot-into-single-user-mode-from-grub))

---

### Post by deadflowr on 2014-02-18
Yeah, I wasn't thinking about the permission versus ownership on this one, but rather the link has a clean copy of the sudoers file.

But on the subject of the rather odd uid(444), I must wonder what it is or who it is
Is there a known system user common to that uid?

---

### Post by fdrake on 2014-02-18
> **deadflowr said:**
> Yeah, I wasn't thinking about the permission versus ownership on this one, but rather the link has a clean copy of the sudoers file.

But on the subject of the rather odd uid(444), I must wonder what it is or who it is
Is there a known system user common to that uid?

i don't know who is uid 444. probably some kind of program? "ls -l /etc/sudoers" will tells us  :D

---

### Post by Impavidus on 2014-02-18
This may be speculation, but I was thinking that OP for some reason tried to modify /etc/sudoers by chmod'ing to 444 for write permission (bad idea anyway), but instead ran chown 444. chmod and chown are often used in the same context, so if you don't understand the whole security system yet it's easy to get confused and swap them.

Anyway, a simple chown root from the recovery console may fix it.

---

### Post by jeanjd63 on 2014-02-18
> **Impavidus said:**
> This may be speculation, but I was thinking that OP for some reason tried to modify /etc/sudoers by chmod'ing to 444 for write permission (bad idea anyway), but instead ran chown 444. chmod and chown are often used in the same context, so if you don't understand the whole security system yet it's easy to get confused and swap them.

Anyway, a simple chown root from the recovery console may fix it.

I'm not sure and if a command chmod or chown as been applied to /etc (see the post #4) a reinstall is the best solution.

---


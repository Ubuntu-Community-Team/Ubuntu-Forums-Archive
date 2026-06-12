---
title: "Can't update system or use su sudo"
date: 2007-01-10
forum: General Help
---

### Post by magpie56 on 2007-01-10
Hi
having problems with my systems - I can no longer use the updater (adept) as it comes up with a dialog box saying 'Su returned with an error' when I try from a terminal  I get 'unable to lookup Magpie-Ubunto via gethostname()'

Can anyone help please?

David

---

### Post by bodhi.zazen on 2007-01-10
See if this helps:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Delkster on 2007-01-10
> **magpie56 said:**
> when I try from a terminal  I get 'unable to lookup Magpie-Ubunto via gethostname()'

Sounds like your computer's hostname hasn't been set correctly, or there's a problem with the hosts configuration file.

Open the terminal (Applications > Accessories > Terminal) and enter the following command:
```
cat /etc/hostname
```
It should say "Magpie-Ubunto", if that's what you set your computer's name to. It's probably correct.

Also in the terminal, enter the following command:
```
cat /etc/hosts
```
Please post the results here so we can try and see if there's something wrong.

---

### Post by magpie56 on 2007-01-10
Hi
Results from terminal

magpie@Magpie-Ubuntu:~$ cat /etc/hostname
Magpie-Ubuntu
magpie@Magpie-Ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Magpie-Ubuntu.MAGPIES

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


David

---

### Post by bodhi.zazen on 2007-01-10
Change

> 127.0.1.1 Magpie-Ubuntu.MAGPIES

To

> 127.0.1.1 Magpie-Ubuntu

You may need to edit from either the failsafe mode or live CD

---


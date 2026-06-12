---
title: "arkose-gui: how?"
date: 2013-01-29
forum: General Help
---

### Post by sanderj on 2013-01-29
Hi,

I'm trying to use arkose-gui with gedit with "sudo arkose-gui gedit". However, that results in:

```
sander@R540:~$ sudo arkose-gui gedit
usage: arkose [--help] [-h] [-p] [-d {none,system,session,both}]
              [-n {none,direct,filtered}] [-s SIZE] [-t {ext4,tmpfs}]
              [-x {none,isolated,direct}] [--root ROOT]
              [--root-type {cow,bind}] [--base-path PATH] [--bind BIND]
              [--cow COW] [--restrict RESTRICT] [--device DEVICE]
              [CMD [CMD ...]]
arkose: error: argument -n/--network: expected one argument
sander@R540:~$

```

Adding "-n direct" doesn't help either:

```
sander@R540:~$ sudo arkose-gui -n direct gedit
usage: arkose [--help] [-h] [-p] [-d {none,system,session,both}]
              [-n {none,direct,filtered}] [-s SIZE] [-t {ext4,tmpfs}]
              [-x {none,isolated,direct}] [--root ROOT]
              [--root-type {cow,bind}] [--base-path PATH] [--bind BIND]
              [--cow COW] [--restrict RESTRICT] [--device DEVICE]
              [CMD [CMD ...]]
arkose: error: argument -n/--network: expected one argument
sander@R540:~$ 
```


Any tips to get it working? 

Thanks.

---

### Post by sanderj on 2013-01-29
Ah, nevermind:

I need to use 'arkose', not arkose-gui

So, this works:

sudo arkose chromium-browser
sudo arkose gedit

---


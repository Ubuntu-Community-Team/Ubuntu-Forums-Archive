---
title: "Starting service without password"
date: 2015-12-07
forum: General Help
---

### Post by glypto on 2015-12-07
Hi,
I'd like to allow selected users to start/stop services without sudo and password, so I added following line using visudo:

username ALL = NOPASSWD: /usr/sbin/service apport stop

However, when when trying to stop service:

$ /usr/sbin/service apport stop

I get a dialogue asking for password : 'authentication is required to manage system services or units'

---

### Post by TheFu on 2015-12-07
That NOPASSWD just means that sudo won't ask for a password.

You'd still need to use:
```
sudo service apport stop
```

Of course, you can make an alias for that.

```
alias sapportstop='sudo service apport stop'

```
and call **sapportstop** from that point on, inside a shell. Name it whatever you want, just be careful about collisions with other program names until you are better with aliases and know to use \sapportstop when you do NOT want an alias used.

Aliases are part of every shell that I know. Mine are placed into ~/.bash_aliases .. but they can be put into almost any startup file for the shell you use to work.

---


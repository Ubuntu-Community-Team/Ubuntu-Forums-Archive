---
title: "docker ps command hanging on lxc container"
date: 2023-02-11
forum: General Help
---

### Post by sniper8752 on 2023-02-11
I am running Ubuntu 22.04 on a lxc container on proxmox.  When I run docker ps, it just hangs.  I tried restarting the service and the container, but the command still hangs.

---

### Post by TheFu on 2023-02-12
Docker isn't lxc any more than lxc is docker.

To run the ps command inside an lxc container with logging into that container, use:
```
$ lxc exec pihole  ps aux
```

I find that using tab completion for manpages will show what's available.  
```
man lxc{tab}{tab} 
```
will ask if you want to see all the available manpages that begin with "lxc" .... if you say Yes, then 200+ results will be paginated.  The lxc command has many options, so to keep the documentation manageable, they will have
command "lxc exec" in an "lxc-exec" manpage.

Depending on what you'd like to know, the "lxc info" or "lxc list" commands might be useful.  Output json, xml, or yaml formats.  Try this:
```
lxc list --format=yaml|egrep 'memory:|disk:|cpu:|usage[:_]|^  name:'
```
Unfortunately, they don't have a --human option to get size output in easy to read amounts.

---

### Post by sniper8752 on 2023-02-13
In proxmox, I am logged into the lxc container, and I can also ssh into it.  the docker container was running before, but now it seems the dockerd is unresponsive.

---


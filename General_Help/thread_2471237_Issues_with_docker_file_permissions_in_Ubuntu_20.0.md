---
title: "Issues with docker file permissions in Ubuntu 20.04"
date: 2022-01-24
forum: General Help
---

### Post by johndid on 2022-01-24
Hi everyone,

I created this volume  for my MotionEye docker container:

```
/media/backup/docker/motioneye/Camera1
```


I gave the folder recursive permissions for my linux user's account. I expected that any time a new folder was created it got user permissions too.
 However, each time the app create automatically a new folder (in Camera1 folder) in which it saves video recordings and images, it got root permissions.
I'd like it to create each new folder with user permissions instead. How can I do that?

Thanks

---

### Post by TheFu on 2022-01-24
I'm fairly certain this is a docker specific question, not normal Unix permissions.
If possible, would be good to edit the threat title to include "docker file permissions"

I can't help with docker, sorry.

---

### Post by johndid on 2022-01-25
> **TheFu said:**
> I'm fairly certain this is a docker specific question, not normal Unix permissions.
If possible, would be good to edit the threat title to include "docker file permissions"

I can't help with docker, sorry.

Ok, I edited the thread title.
You might be right. It could be a docker permission issue.
Anyway, someone told me that I should have added a couple of lines to my yml file before running it and creating the container, something like:

```

[B]environment:
  - PUID=1000
  - PGID=1000
[/B]
```
Not sure that it would work though.
Thanks

---

### Post by TheFu on 2022-01-25
> **johndid said:**
> Ok, I edited the thread title.
You might be right. It could be a docker permission issue.
Anyway, someone told me that I should have added a couple of lines to my yml file before running it and creating the container, something like:

```

[B]environment:
  - PUID=1000
  - PGID=1000
[/B]
```
Not sure that it would work though.
Thanks

I use a different container method and force the root UID/GID to be 100000.  The main security provided by Linux containers is NOT having local users mapped into users inside the container. Security is a 2-way issue. If you can get into the container, then they can get out.  May as well just use a lighter, sandbox, method like a snap package or firejail, instead of a full container if having UIDs break the container veil is the intention.  IMHO.  But I could be missing something very important.  

Perhaps docker does something different, but since they are all built using cgroups, I don't see how.

---

### Post by johndid on 2022-01-25
> **TheFu said:**
> I use a different container method and force the root UID/GID to be 100000.  The main security provided by Linux containers is NOT having local users mapped into users inside the container. Security is a 2-way issue. If you can get into the container, then they can get out.  May as well just use a lighter, sandbox, method like a snap package or firejail, instead of a full container if having UIDs break the container veil is the intention.  IMHO.  But I could be missing something very important.  

Perhaps docker does something different, but since they are all built using cgroups, I don't see how.

I have no idea if I can do what you said above with docker.
As far as I know, they suggest not to create and run docker containers as root.

Thanks anyway.

---

### Post by TheFu on 2022-01-25
> **johndid said:**
> I have no idea if I can do what you said above with docker.
As far as I know, they suggest not to create and run docker containers as root.

Thanks anyway.

A UID of 100000 isn't root. For a very long time, docker only ran containers as root. It was a pretty big flaw in that implementation.

The manpage for **subuid** explains the local to container uid mappings. I know that LXD containers use this file.
The **user_namespaces** and **cgroup_namespaces** manpages have an overview of how these basic kernel capabilities actually work, which is what all Linux Containers are based on.

---


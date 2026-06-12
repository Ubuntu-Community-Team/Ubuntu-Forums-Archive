---
title: "update error after fresh install of 16.04"
date: 2017-05-14
forum: General Help
---

### Post by offir on 2017-05-14
i install ubuntu 16.04 
did some update
and install Several software and games
now when i open update software
i get this error

```
W:The repository 'http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:Failed to fetch http://archive.ubuntugames.org/dists/ubuntugames/InRelease  Temporary failure resolving 'archive.ubuntugames.org', E:Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/source/Sources  404  Not Found, W:Some index files failed to download. They have been ignored, or old ones used instead.
```

how can i fix it ?

---

### Post by Dennis N on 2017-05-14
Looks like there are no packages for 16.04 (xenial) in that PPA. 
See: [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/)
Uncheck the box by that PPA in Software Sources and Reload.

---

### Post by offir on 2017-05-14
i remove the v from the box
but It still happens

---

### Post by RobGoss on 2017-05-14
You have to uncheck or remove, the PPA's listed in that error message once that is done reload the system and try again....

---

### Post by Dennis N on 2017-05-14
Also from your first post:

> W:Failed to fetch [http://archive.ubuntugames.org/dists/ubuntugames/InRelease](http://archive.ubuntugames.org/dists/ubuntugames/InRelease)  Temporary failure resolving 'archive.ubuntugames.org'

This is probably the cause of the continued problem. Seems more than temporary after this much time. I get "Server not Found" when trying to access that URL or even the domain.

If you want to avoid the "Failed to download repository information" you should also uncheck the archive.ubuntugames.org repositories in that sources list, since it is not responding.

---


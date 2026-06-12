---
title: "Problem with updating. How do I remove repository?"
date: 2016-05-02
forum: General Help
---

### Post by jcer93705 on 2016-05-02
```
W:The repository 'http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:The repository 'http://ppa.launchpad.net/moorkai/cinnamon/ubuntu xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., E:Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found, E:Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found, E:Failed to fetch [http://ppa.launchpad.net/moorkai/cinnamon/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/moorkai/cinnamon/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found, E:Failed to fetch [http://ppa.launchpad.net/moorkai/cinnamon/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/moorkai/cinnamon/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Hi problem above. So I want to remove repository of cairo dock. by software and updates I cant uncheck it or select remove why? Ty

---

### Post by claracc on 2016-05-02
The straightforward way is open software updates, click on settings, other software tab, and there, you uncheck the repositories you want to disable, then close and changes will be updated. 

Other way is to edit in a xterm, file /etc/apt/sources.list, there you write a # sign before the line with the repository address you want to remove,then save and close and try updating again.

---

### Post by Bucky Ball on 2016-05-02
> **claracc said:**
> Other way is to edit in a xterm, file /etc/apt/sources.list, there you write a # sign before the line with the repository address you want to remove,then save and close and try updating again.

As you've tried and failed with claracc's first suggestion, try this. You will need to open the file as root. 

```
sudo nano /etc/apt/sources.list
```

Information on how to remove or disable a repository is widely available on the web. '[remove ppa ubuntu]("https://duckduckgo.com/?q=remove+ppa+ubuntu")'

---


---
title: "Problems setting up SVN with svnserve"
date: 2013-04-12
forum: General Help
---

### Post by tuner23 on 2013-04-12
Hy,


we want to migrate from http to svnserve, but i can't get the daemon working.

When i try to do a checkout i always get a senseless:
```

svn: generic failure

```

Daemon seems to work, cause when i checkout wrong reposit i get
```

svn: No repository found

```

Also most solutions i found for this error while searching on the web characterise the error as a resolvin eroor, so i setup hostname and fqdn.

And i set up a complete new machine and repos, with no effect.

The site(s) i used for setting up the server:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)
[http://skovalev.de/2010/01/29/svn-server-unter-ubuntu-installieren/](http://skovalev.de/2010/01/29/svn-server-unter-ubuntu-installieren/)

Also with strace -f i found no errors and
I have now really no idea left, what the problem could be and the error-message is not really helpfull..


Has someone an idea, where the problem could be? I use 12.04 LTS


Thanks in advance,
Antonios.

---


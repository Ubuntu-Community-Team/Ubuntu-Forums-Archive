---
title: "aptitude / Synaptic problem"
date: 2007-12-09
forum: General Help
---

### Post by cjbailey1 on 2007-12-09
I've had an annoying one appear over the last few days.

A week or so ago I installed GNUCash from the package manager, which was fine until the other day when the program stopped working.  I then went and removed the package using Synaptic Package Manager and discovered that it was saying no package was available.  I then tried to update the package list, which gave me the following error:

```

Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)

```

I removed all but the main repositories and then tried various different servers (Main server, US server, third party mirrors, etc.) but keep getting the same error (with different server addresses).  I've tried cleaning down the package lists to no avail.  I have even re-installed Aptitude, Synaptic and associated packages.

Help!

---

### Post by plucky on 2007-12-09
See [thread=621059]here[/thread]

---

### Post by cjbailey1 on 2007-12-09
> **plucky said:**
> See [thread=621059]here[/thread]

Thank you for that , I'm updating again at the moment.  I did do a search through the forum and failed to spot that earlier thread.  I am intrigued as to where 'web' came from in each of those three commands.

---


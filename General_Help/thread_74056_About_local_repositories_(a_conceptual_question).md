---
title: "About local repositories (a conceptual question)"
date: 2005-10-10
forum: General Help
---

### Post by blastus on 2005-10-10
I want to create a local repository, burn it, install Ubuntu, and then the contents of the CD repository. I just I want to do a base Ubuntu installation--I do not care at this point if it is out-of-date.

The problem with creating a local repository is the cache. It is obvious that the CD repository is going to get quickly out-of-date. Therefore, if "apt-get update" has been run while connected to the Internet, the CD repository is going to be useless. For example, let's say that:

The Ubuntu installation CD contains:
libwhatever2.5.deb
libwhereever3.0.deb

My CD repository contains:
libwhatever2.6.deb
libwhereever3.1.deb

The Ubuntu repositories contain:
libwhatever2.7.deb
libwhereever3.2.deb

Now if "apt-get update" is run, the CD repository isn't even going to be used because it is out-of-date. The only solution I can think of is to add the CD repository to /etc/apt/sources.list and comment out ALL the other repositories. Is there an easier way to do this?

---

### Post by Leif on 2005-10-10
don't run update ?

---


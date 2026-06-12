---
title: "[SOLVED] I think synpatic package manager is corrupted"
date: 2008-06-08
forum: General Help
---

### Post by nerd0795 on 2008-06-08
Well, I tried to install jokosher (another post and it said...

```
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gnonlin/gstreamer0.10-gnonlin_0.10.9-1_i386.deb
  404 Not Found


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-pkg-resources_0.6c8-0ubuntu2_all.deb
  404 Not Found


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c8-0ubuntu2_all.deb
  404 Not Found


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/j/jokosher/jokosher_0.9-0ubuntu1_all.deb
  404 Not Found
```

Then I tried to install the google gadgets.

When I refreshed my software sources it wasn't able to refresh them all giving me the same error.

Then I tried downloading it and it gave me the same error when it finished the first file.

I am using ubuntu 8.04.

( I did post a forum about the first error but after I fond a few more I posted this one)

I hope this was the right place to post it.

---

### Post by drs305 on 2008-06-08
Some have said some Canadian repositories are down. In synaptic, try Settings > Repositories, Download from: > Other, Select Best Server. Choose Server, Close. After doing this try running your commands again.

---

### Post by nerd0795 on 2008-06-08
Tried donwloading jokosher again and I got this >.<

```
E: I wasn't able to locate file for the gstreamer0.10-gnonlin package. This might mean you need to manually fix this package.
```

---

### Post by drs305 on 2008-06-08
I just successfully downloaded it from the U.S. archive.linux.duke.edu repository...

---

### Post by Bubba64 on 2008-06-08
Do you have all the repositories ticked on except source.

---

### Post by nerd0795 on 2008-06-08
I just downloaded that gstream thing from synpatic and now it works.  (I selected main server)

---


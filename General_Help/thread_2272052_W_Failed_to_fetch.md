---
title: "W: Failed to fetch"
date: 2015-04-03
forum: General Help
---

### Post by calvin16 on 2015-04-03
Running sudo apt-get update I get 3 W: Failed to fetch errors and one E: Some index files failed to download error. Looking in my sources.list file I cannot seem to find the addresses that are failing to fetch. Anyway to clean this mess up?

```

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/utopic-getdeb/games/binary-amd64/Packages  416  Requested Range Not Satisfiable [IP: 104.28.24.125 80]


W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by deadflowr on 2015-04-03
Open Software and Updates, go to Other Software and remove the entries for tualatrix and getdeb.

There is no ppa for utopic for the tualatrix ppa.
(You can add the tualatrix-next ppa, but not the regular ppa for utopic
found here
[https://launchpad.net/~tualatrix/+archive/ubuntu/next](https://launchpad.net/~tualatrix/+archive/ubuntu/next)

As far as the getdeb ppa, how'd you add it.
And also, the getdeb repos tend to go down here and there, so that is something to consider...

---

### Post by calvin16 on 2015-04-03
Thank you kindly. That fixed the issue. As for how I got the getdeb ppa, I dont know. It's a pretty new installation of Ubuntu with the Gnome Flashback shell installed. Not sure if that did it or not, but either way its fixed. Thank you sir.

---

### Post by Frogs Hair on 2015-04-03
The ppa name was changed for 14.10.

[https://launchpad.net/~tualatrix/+archive/ubuntu/next](https://launchpad.net/~tualatrix/+archive/ubuntu/next)

---


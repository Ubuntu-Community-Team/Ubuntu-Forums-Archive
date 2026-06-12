---
title: "Problem whit apt-get update"
date: 2017-03-30
forum: General Help
---

### Post by tokar93 on 2017-03-30
I end up whit this error when i run apt-get update. Any suggestion on what i can do to fix this? 
  ```
root@server1:~# apt-get update
Err:1 [http://apt.izzysoft.de/ubuntu](http://apt.izzysoft.de/ubuntu) generic InRelease
  Temporary failure resolving 'apt.izzysoft.de'
Err:2 [http://apt.newrelic.com/debian](http://apt.newrelic.com/debian) newrelic InRelease
  Temporary failure resolving 'apt.newrelic.com'
Err:3 [http://software.virtualmin.com/gpl/ubuntu](http://software.virtualmin.com/gpl/ubuntu) virtualmin-xenial InRelease
  Temporary failure resolving 'software.virtualmin.com'
Err:4 [http://ppa.launchpad.net/ondrej/apache2/ubuntu](http://ppa.launchpad.net/ondrej/apache2/ubuntu) xenial InRelease
  Temporary failure resolving 'ppa.launchpad.net'
Err:5 [http://software.virtualmin.com/gpl/ubuntu](http://software.virtualmin.com/gpl/ubuntu) virtualmin-universal InRelease
  Temporary failure resolving 'software.virtualmin.com'
Err:6 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) xenial InRelease
  Temporary failure resolving 'ppa.launchpad.net'
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:9 [https://deb.nodesource.com/node_4.x](https://deb.nodesource.com/node_4.x) xenial InRelease
  Could not resolve host: deb.nodesource.com
Err:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://software.virtualmin.com/gpl/ubuntu/dists/virtualmin-xenial/InRelease](http://software.virtualmin.com/gpl/ubuntu/dists/virtualmin-xenial/InRelease)  Temporary failure resolving 'software.virtualmin.com'
W: Failed to fetch [http://software.virtualmin.com/gpl/ubuntu/dists/virtualmin-universal/InRelease](http://software.virtualmin.com/gpl/ubuntu/dists/virtualmin-universal/InRelease)  Temporary failure resolving 'software.virtualmin.com'
W: Failed to fetch [http://apt.izzysoft.de/ubuntu/dists/generic/InRelease](http://apt.izzysoft.de/ubuntu/dists/generic/InRelease)  Temporary failure resolving 'apt.izzysoft.de'
W: Failed to fetch [http://apt.newrelic.com/debian/dists/newrelic/InRelease](http://apt.newrelic.com/debian/dists/newrelic/InRelease)  Temporary failure resolving 'apt.newrelic.com'
W: Failed to fetch [https://deb.nodesource.com/node_4.x/dists/xenial/InRelease](https://deb.nodesource.com/node_4.x/dists/xenial/InRelease)  Could not resolve host: deb.nodesource.com
W: Failed to fetch [http://ppa.launchpad.net/ondrej/apache2/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/ondrej/apache2/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'ppa.launchpad.net'
W: Failed to fetch [http://ppa.launchpad.net/ondrej/php/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/ondrej/php/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'ppa.launchpad.net'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bashing-om on 2017-03-30
tokar93; Hello; Welcome to the forum.

Those responses make me question that you have internet connectivity .
What results from terminal commands:
```

ping -c3 archive.ubuntu.com
ping -c3 8.8.8.8

```

[INDENT][INDENT]a failure to communicate ?
[/INDENT][/INDENT]

---


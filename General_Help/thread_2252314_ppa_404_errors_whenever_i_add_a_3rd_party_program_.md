---
title: "ppa 404 errors whenever i add a 3rd party program ppa"
date: 2014-11-10
forum: General Help
---

### Post by TheRacerX on 2014-11-10
anything i add a ppa thats not a ubuntu repository such as openshot or ubuntu tweak it gives me a 404 error [ATTACH=CONFIG]257884[/ATTACH]

---

### Post by claracc on 2014-11-11
Could you post the url address of ppas you are trying to add an obtain 404 "not found error?

---

### Post by TheRacerX on 2014-11-11
here is the urls that show up in the terminal 

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  Bad header line


W: Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by claracc on 2014-11-11
About first error: W: Failed to fetch [http://linux.dropbox.com/ubuntu/dist...amd64/Packages](http://linux.dropbox.com/ubuntu/dist...amd64/Packages) Bad header line it would be good you post here (between code tags) your /etc/apt/sources.list since as error says he line in the file can be malformed.

About the other two errors 

W: Failed to fetch [http://ppa.launchpad.net/me-davidsan...amd64/Packages](http://ppa.launchpad.net/me-davidsan...amd64/Packages) 404 Not Found
W: Failed to fetch [http://ppa.launchpad.net/openshot.de...amd64/Packages](http://ppa.launchpad.net/openshot.de...amd64/Packages) 404 Not Found

You obtain what you have to obtain since the package software addressed are not in this server. You have to look for other ppas with the same software which haven't been removed from server.

What is the ubuntu release you are using?

---

### Post by TheRacerX on 2014-11-11
im using Ubuntu 14.10 64bit with Unity Desktop

---

### Post by buzzingrobot on 2014-11-11
> **TheRacerX said:**
> im using Ubuntu 14.10 64bit with Unity Desktop

Seems Dropbox hasn't yet created a 14.10/Utopic directory on their server.  I'd just install nautilus-dropbox from the repos, or download the latest .deb from here: [https://linux.dropbox.com/ubuntu/pool/main/](https://linux.dropbox.com/ubuntu/pool/main/), if that's the issue.

---

### Post by TheRacerX on 2014-11-11
what about openshot and clementine they both have file updates for utopic so they should be working.

---

### Post by oldos2er on 2014-11-11
[http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/) only shows releases up to quantal, and [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/) to trusty.

---


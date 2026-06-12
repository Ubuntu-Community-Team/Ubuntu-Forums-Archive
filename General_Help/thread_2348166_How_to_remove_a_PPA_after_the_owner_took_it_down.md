---
title: "How to remove a PPA after the owner took it down"
date: 2017-01-01
forum: General Help
---

### Post by jonathan90 on 2017-01-01
I've been getting this error message saying "This update information is outdated." It asked me to check for updates, and when I clicked on it, it said there was a network error. When I ran sudo apt-get update, it gave this message.

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/varlesh-l/papirus-pack/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/varlesh-l/papirus-pack/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/varlesh-l/papirus-pack/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/varlesh-l/papirus-pack/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

I looked for the Papirus PPA on Launchpad and couldn't find it. I'm guessing that is the cause of the update error. How can I remove the Papirus PPA? Thanks!

---

### Post by cariboo on 2017-01-01
The easy GUI way is to go to System Settings->Software & Updates->Other Software, and remove from there.

You can also use ppa-purge:

```
sudo apt-get install ppa-purge
```

the run the following command in a terminal:

```
sudo ppa-purge ppa_name
```

---


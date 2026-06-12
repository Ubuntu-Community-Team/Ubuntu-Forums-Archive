---
title: "Update errors"
date: 2015-05-10
forum: General Help
---

### Post by Tanner_White on 2015-05-10
I'm getting a few errors when running updates. Here is the output:

> W: Failed to fetch [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease)  

W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/aftershot/ubuntu/dists/utopic/main/binary-amd64/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/aftershot/ubuntu/dists/utopic/main/binary-amd64/Packages)  HttpError404

W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/aftershot/ubuntu/dists/utopic/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/aftershot/ubuntu/dists/utopic/main/binary-i386/Packages)  HttpError404

W: Some index files failed to download. They have been ignored, or old ones used instead.

These are occurring after upgrading from 14.10 to 15.04. How can I fix this?

Thank you much.

---

### Post by grahammechanical on 2015-05-10
Before upgrading we should disable any PPAs. The upgrade process should also disable any PPAs because a PPA that exists for one version of Ubuntu might not exist for another version of Ubuntu.

If you go to software & updates you can disable those PPAs and the error messages will go away. You need to find out if there is a spotify PPA for 15.04.

Regards.

---


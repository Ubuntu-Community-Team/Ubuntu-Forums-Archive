---
title: "Can snaps write to /media? How?"
date: 2016-10-24
forum: General Help
---

### Post by HittingSmoke on 2016-10-24
I have an Ubuntu 16.04 VM I'm trying to get configured as a NextCloud server. I have a bare metal NAS that is serving files via NFS shares.

I've installed the NextCloud snap from the official repo but I'm having trouble getting the NextCloud server to write to the NFS share. The NFS share is mounted at /media/nas so snaps can have access to it.

The NFS share is configured correctly with R/W access. From the command line I can write to the NFS share with root, my local user, or www-data.

The web server serving NextCloud from within the snap is Apache and httpd appears to be running as root.

However from the NextCloud interface I can not create files. It just says "Can't create file..." The PHP logs are not helpful. They just report permission denied.

Is there a way to allow the NextCloud snap to write to my NFS share?

---


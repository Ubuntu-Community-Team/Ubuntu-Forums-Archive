---
title: "Ubuntu Server For NAS and NVR"
date: 2017-02-21
forum: General Help
---

### Post by tiptricky2 on 2017-02-21
Is it possible to use ubuntu server as a nas for both videos and NVR? If so what software do you guys recommend?

---

### Post by TheFu on 2017-02-21
Sure.
As a NAS, I use normal file systems, but have excellent backups.  Also use Plex Server to make photos, audio, video available to pretty much any device on my network. That includes when I'm traveling - via a VPN. No plex account needed.  No need to use tricks to merge different disks into a single file system needed. Plex understands having different back-end storage under the same "type" of media.

Many people use ZFS or BTRFS for their NAS stuff.

I use NFS for storage access from clients. Native Linux/Unix permissions is a must-have for me.

Can't help with NVR. I simply capture an image from a webcam every 30 seconds and save the file with a time stamp.  Daily, a script removes any image files from that directory older than 7 days. I like to do this sort of stuff myself, simple scripts.

---

### Post by gordintoronto on 2017-02-22
For your NVR, do you want just a local camera, or remote or multiple cameras?

---


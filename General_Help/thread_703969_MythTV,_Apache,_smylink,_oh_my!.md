---
title: "MythTV, Apache, smylink, oh my!"
date: 2008-02-21
forum: General Help
---

### Post by hattriq27 on 2008-02-21
Issue:

MythWeb displays the link of a video file as:

```
http://192.168.x.x/mythweb/data/video/**/storage**/Movies/Drama/Across.the.Universe.avi
```

I bolded the issue.  I Linked the default /var/lib/mythtv/video to a secondary drive mounted as /storage.  The command I used was:

```
ln -s /storage/media /var/lib/mythtv/video
```

/storage is a mounted secondary hard drive.  /media is a directory on /storage where my avi file are kept.

Mythweb and apache work fine but then for some reason the links suddenly show up with /storage in them which means I can not click on the link to stream or copy if.

Where is apache (or myth) getting confused?  If I break the link and recreate it, it will be fine for an hour or so.

---


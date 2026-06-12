---
title: "rsync help - one file in multiple sub directories"
date: 2007-10-31
forum: General Help
---

### Post by hawkbane on 2007-10-31
Ok, I know this might not be the best place to post this, but in looking around the web, I haven't found a better location, so I will try here.  Here is the situation:  I manage synchronizing two image servers that host thousands of images.  All of our images are held in sub directories from one root directory (eg: /images/client1, /images/client2, etc).  I need an rsync script that will pull one commonly named file from each of these folders and upload them to the other server (eg: /images/client1/thumb.png, /images/client2/thumb.png, etc).  Here is what I am currently attempting:

```
rsync -r --include-from="filter.txt" /images/ remoteRsyncHost::targetDir/images
```

and the filter.txt file contents:

```
+ /images
+ /images/*
+ /images/*/thumb.png
- *
```

This is not working ... no files are transferred.  Any ideas?

---


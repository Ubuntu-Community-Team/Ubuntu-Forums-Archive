---
title: "wrong symlink"
date: 2007-01-13
forum: General Help
---

### Post by Dilutu on 2007-01-13
Hi 
/dev/video points to /dev/video1394-0, how can I change it to point to  /dev/video0  and make it stick?

---

### Post by NeoLithium on 2007-01-13
I believe it's
```

sudo ln -s /dev/video /dev/video0 

```

---

### Post by cylon359 on 2007-01-13
You could black list the video1394 module maybe...

---

### Post by Dilutu on 2007-01-13
When I do "sudo ln -s /dev/video /dev/video0", I get:
ln: creating symbolic link `/dev/video0' to `/dev/video': File exists.
I need the module "videdo1394-0" to be loaded, but I dont need /dev/video to point to it.

---

### Post by cylon359 on 2007-01-13
sudo ln -sf video0 /dev/video

The -f option overwrites the file if present, and the name of the link comes second.  It isn't a persistent change though.

---

### Post by Dilutu on 2007-01-13
"sudo ln -sf video0 /dev/video"  works good, but  for current session only!

---

### Post by Dilutu on 2007-01-14
Thank you all but I finally commented out the creation of symlink "video" in udev,then I created a file named "10-local.rules" which creates /dev/video and all is ok now!!!

---


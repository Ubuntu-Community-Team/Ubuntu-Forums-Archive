---
title: "Gnomemeeting errors"
date: 2005-10-22
forum: General Help
---

### Post by Zymous on 2005-10-22
I have an eyetoy camera and I've installed the drivers from [http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page](http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page)

The camera now well works with Camorama and xawtv and less well with gqcam (a jerky picture - although it did seem to work at one stage), but not at all with Gnomemeeting. It appears to have problems opening /dev/video0

The permissions on /dev/video*  look like this

lrwxrwxrwx  1 root video    11 2005-10-22 15:57 /dev/video -> /dev/video0
crw-rw----  1 root video 81, 0 2005-10-22 15:01 /dev/video0

The user is a member of the video group.

Any suggestions on where Gnomemeeting logs its errors?

Any suggestions on how to get Gnomemeeting to work with this camera?

Thanks in advance.

-- 
Zym

---


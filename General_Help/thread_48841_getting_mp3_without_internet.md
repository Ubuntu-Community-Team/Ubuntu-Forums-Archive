---
title: "getting mp3 without internet"
date: 2005-07-14
forum: General Help
---

### Post by Basu on 2005-07-14
Hello all. I just installed Ubuntu two days. I would really like to know how I can get mp3 support for it. Unfortunately I can't use the internet as my modem won't work. I will have to download packages separately and then install them. Step by step instructions would be appreciated.

---

### Post by badrinarayan on 2005-07-14
**Disclaimer:I haven't tested it yet**

Assuming you are on i386 architecture (Pentium PCs), download the following
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.8-1ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.8-1ubuntu4_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-1_i386.deb)

Go to the directory where you downloaded these files and type this in the command prompt.
```
sudo dpkg -i gstreamer-0.8-mad_0.8.8-1ubuntu4_i386.deb libid3tag0_0.15.1b-3_i386.deb libmad0_0.15.1b-1_i386.deb

```

This should install mp3 support for rhythmbox, totem etc.,

Regards
Badri

---

### Post by Basu on 2005-07-15
Thanks it worked. But volume is very low, even when control is at the highest. Any suggestions?

---

### Post by maruchan on 2005-07-15
Double-click the speaker icon on your panel. A complete mixer should come up. Is "PCM" turned way up?

---


---
title: "vmware couldn't load the image file after move to another directory"
date: 2007-04-07
forum: General Help
---

### Post by signalat on 2007-04-07
i have vmware player installed on my fesity. at first i put the image file on my home directory. it works well. now, after i moved the image to another directory which has larger free disk space, vmware couldn't load that image file again. anybody knows how to fix it?

---

### Post by spankymasterc on 2007-04-07
did u place it on a ntfs or another format not ext3? becuase if so then u cannot run it from a ntfs i tried it before :D

---

### Post by yabbadabbadont on 2007-04-07
> **signalat said:**
> i have vmware player installed on my fesity. at first i put the image file on my home directory. it works well. now, after i moved the image to another directory which has larger free disk space, vmware couldn't load that image file again. anybody knows how to fix it?

Edit the vmx file for that image and change the path to the files that you moved.  The file path for the various files used are stored in the vmx files.

---

### Post by signalat on 2007-04-07
> **spankymasterc said:**
> did u place it on a ntfs or another format not ext3? becuase if so then u cannot run it from a ntfs i tried it before :D

yeah, i moved it to a ntfs partition.  but, file format shouldn't affect vmware, that's kind of stupid. anyway, i'd better move it back to ext3 partition.

---


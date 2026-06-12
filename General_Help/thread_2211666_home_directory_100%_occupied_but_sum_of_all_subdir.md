---
title: "home directory 100% occupied but sum of all subdirectories less than 10%"
date: 2014-03-17
forum: General Help
---

### Post by dieter-erich on 2014-03-17
I run ubuntu 12.04 under wubi and have about 20 GB total space available. When running a specific program (relion) under /host/ after some time the home directory fills and finally goes to 100% occupancy. However, when trying to find which directory/file has become so big I cannot find anything bigger than some 100 MB and all add up to much less than the 20 GB (var, etc, usr, etc. are much smaller). Thanks for hints as to find out what is growing so much to finally occupy the whole partition.

---

### Post by claracc on 2014-03-17
Perhaps it is some specific and hidden file for relion, i.e.: .relion you can look in your home folder for hidden files wich usually begin with . (dot and the name of file), from a xterm you can obtain a list of all files (hidden and not hidden) with command:

```
ls -la
```

---

### Post by monkeybrain20122 on 2014-03-17
wubi is buggy and weird and it is no longer supported. It has some size limit due to it being installed in Windows. Do a real install if you want to use Ubuntu. Wubi is for demo only (moreover not many people here will be able to help you with wubi because most of us don't use it)

---

### Post by dieter-erich on 2014-03-17
Thanks for your comments! I finally found that .xsession-errors.old had grown to 9.5 GB with (obviously) a lot of messages. Deleting it restored functionality, although it is not quite clear to me what is being written to this file. 

Nevertheless, I am quite happy with wubi, especially because it is so easy to backup, to be removed and even to have several versions of ubuntu on the same machine. You just copy it and fool around with the copy without any danger :-))

---

### Post by monkeybrain20122 on 2014-03-17
> **dieter-erich said:**
> 
Nevertheless, I am quite happy with wubi, especially because it is so easy to backup, to be removed and even to have several versions of ubuntu on the same machine. You just copy it and fool around with the copy without any danger :-))

And you need to have Windows in several machines in the first place.

It is easy to copy Ubuntu to several places and mess around without danger, but to really know it you have to stop relying on Windows.

---

### Post by claracc on 2014-03-18
> **dieter-erich said:**
> Thanks for your comments! I finally found that .xsession-errors.old had grown to 9.5 GB with (obviously) a lot of messages. Deleting it restored functionality, although it is not quite clear to me what is being written to this file. 

Nevertheless, I am quite happy with wubi, especially because it is so easy to backup, to be removed and even to have several versions of ubuntu on the same machine. You just copy it and fool around with the copy without any danger :-))

You are welcome.

Please, mark the thread as solved with thread tools in order to help others with similar problems.

Thanks.

---


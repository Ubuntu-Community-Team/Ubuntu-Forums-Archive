---
title: "Xsane doesn't work after upgrade from 14.04LTS to 16.04LTS"
date: 2016-08-23
forum: General Help
---

### Post by undefer on 2016-08-23
Hello!
Xsane says only "Failed to start scanner: Error during device I/O" after upgrade from 14.04LTS to 16.04LTS.
My scanner is Canon, Inc. CanoScan LiDE 110.
I tried to run xsane as root.
After many attempts to scan I have scanned several images, but after it xsane again is not working.
xsane haven't --verbose option, so I even don't know how to get more information.

---

### Post by ventrical on 2016-08-23
I am not 100% sure this is your problem  but  during the upgrade from 14.04 to 16.04 there is an interactive process which asks us if we want to remove/replace/delete obsoleted files. if we choose no it could affect any given program and if we choose yes it could also affect. I do not know if removing and re-installing xsane would help. It could be a config file.

Regards..

---

### Post by undefer on 2016-08-23
> interactive process which asks us if we want to remove/replace/delete obsoleted files.

Yes, I remember that one xsane config file was changed and it asked me replace/leave my version. And I have selected "replace". Don't remember what the file, but seems there was something about hp. And I have not hp scanner.
Have tried reinstall xsane. No any changes.

---

### Post by undefer on 2016-09-06
I have reinstalled my 16.04 with upgrade from i386 to amd64 and now xsane again works.

---


---
title: "No package 'glib-2.0' found"
date: 2004-10-31
forum: General Help
---

### Post by ToWAH on 2004-10-31
gxine-0.3.3

checking for glib-2.0 >= 2.0.0... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found

configure: error: Library requirements (glib-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Help!!

---

### Post by oddabe19 on 2004-10-31
easy...

follow the ubuntu multimedia how to  and install mplayer...  :-P 

or uncomment universe in /etc/apt/sources.list and add 
```
#Multimedia
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

then ```
sudo apt-get update && sudo apt-get install gxine
```

that should work.

---

### Post by ToWAH on 2004-10-31
gxine works
thanks but  
have a bit problem to cdrom & dvd rom permission
and still cant compile xine hehe error persist

---


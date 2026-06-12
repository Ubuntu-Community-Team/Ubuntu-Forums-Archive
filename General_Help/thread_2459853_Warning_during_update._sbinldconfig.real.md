---
title: "Warning during update. /sbin/ldconfig.real"
date: 2021-03-27
forum: General Help
---

### Post by rsteinmetz70112 on 2021-03-27
During a routine update of a 32 bit 18.04LTS server I got the messages below.

```
/sbin/ldconfig.real: /usr/lib/libpt.so.2.10.11 is not a symbolic link
```

The first one is correct,  /usr/lib/libpt.so.2.10.11 is a file. But I'm not sure what it should be a link to, if anything.

```
# ls -ld ldconfig*
-rwxr-xr-x 1 root root    387 Dec  7 10:38 ldconfig
-rwxr-xr-x 1 root root 805872 Dec  7 10:38 ldconfig.real
```


```
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf: No such file or directory
```

The second one points to a link

```
:/etc/ld.so.conf.d# ls -ld *
-rw-rw-r-- 1 root root  36 Mar 24  2014 fakeroot-i386-linux-gnu.conf
-rw-r--r-- 1 root root 168 Dec  7 10:38 i386-linux-gnu.conf
**lrwxrwxrwx 1 root root  41 Apr 18  2015 i386-linux-gnu_EGL.conf -> /etc/alternatives/i386-linux-gnu_egl_conf**
```

That link points to another link

```
:/etc/alternatives# ls -ld i386*
lrwxrwxrwx 1 root root 48 Feb 14 16:55 i386-linux-gnu_egl_conf -> **/usr/lib/i386-linux-gnu/libhybris-egl/ld.so.conf**
```

Which in turn points to an empty file.

```
:/usr/lib/i386-linux-gnu/libhybris-egl# ls -ld ld.so.conf
-rw-r--r-- 1 root root 0 Mar 27 13:58 ld.so.conf
```

I'm not sure if any of this is significant or simply left over from previous upgrades that were not cleaned up properly.

---


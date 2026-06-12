---
title: "apt-get problem"
date: 2005-09-09
forum: General Help
---

### Post by war-totem on 2005-09-09
```
root@ubuntu:/home/lightbringer # apt-get install vlc
Reading Package Lists... Done
Building Dependency Tree... Done
vlc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gaim (1.1.2-3ubuntu1-4.10ubp1) ...
rmdir: `/usr/share/doc/gaim': No such file or directory
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gaim
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

after i just finished dist-upgrade apt-get has been whining about error processing gaim, even though im not attempting to process gaim.

also, i have gdesklets installed but when i run it in a shell i get: 

```
/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)
``` 

and it hangs. any clues?

---

### Post by amohanty on 2005-09-09
> vlc is already the newest version. 

This means the latest version of vlc is already installed and you dont need to do anything.

HTH
AM

---

### Post by angkor on 2005-09-10
please don't double post in different forums 

[http://ubuntuforums.org/showthread.php?t=64020](http://ubuntuforums.org/showthread.php?t=64020)

You could / should have continued your thread there.

---


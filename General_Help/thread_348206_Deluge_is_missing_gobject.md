---
title: "Deluge is missing gobject"
date: 2007-01-28
forum: General Help
---

### Post by jae1227 on 2007-01-28
Every time I try to run deluge I get this error:

```
justin@fish:~$ deluge
Traceback (most recent call last):
  File "deluge.py", line 26, in <module>
    import gobject
ImportError: No module named gobject
```

I thought python-gobject was missing but I guess not:

```
justin@fish:~$ sudo apt-get install python-gobject
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gobject is already the newest version.
The following packages were automatically installed and are no longer required:
  libseda-java libcommons-cli-java libgtk-jni libcairo-java libbcprov-java
  libglib-java libgtk-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gnome-app-install (0.2.21) ...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 12, in <module>
    import xdg.DesktopEntry
ImportError: No module named xdg.DesktopEntry
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-app-install
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
justin@fish:~$ 
```

I hope someone could make sense out of this

---

### Post by jae1227 on 2007-01-29
I guess I will have to spend this weekend reinstalling Ubuntu...

---

### Post by Anicka on 2007-01-30
Check that you have python 2.4 and python-xdg properly installed, then check where python is installed ("whereis python"), it should be in /usr/bin and in /usr/share. If you have anything in /usr/local/bin, apt and aptitude will by some mysterious reason use that no matter how well you have defined your pythonpath. What I did was to brutally delete all python files in /usr/local/bin and the corresponding lib-files and it worked.

---

### Post by jae1227 on 2007-01-30
> **Anicka said:**
> Check that you have python 2.4 and python-xdg properly installed, then check where python is installed ("whereis python"), it should be in /usr/bin and in /usr/share. If you have anything in /usr/local/bin, apt and aptitude will by some mysterious reason use that no matter how well you have defined your pythonpath. What I did was to brutally delete all python files in /usr/local/bin and the corresponding lib-files and it worked.

You are GREAT!!! :D Yeah I just deleted everything relating to python in my /usr/local/bin then I did

```
sudo apt-get install deluge
```

And then it worked. I was so weird because I used deluge back when it was 0.3 but this last month I had been forced to use the slow azureus b/c deluge was giving my that error. Thanks again for helping me out.

---

### Post by Anicka on 2007-01-30
> **jae1227 said:**
> Thanks again for helping me out.

No problem, only happy I could help. :)

---


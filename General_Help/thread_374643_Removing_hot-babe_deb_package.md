---
title: "Removing hot-babe deb package"
date: 2007-03-02
forum: General Help
---

### Post by srunni on 2007-03-02
Hi, 
I installed the hot-babe monitoring app from the deb available at their site ([http://dindinx.net/hotbabe/](http://dindinx.net/hotbabe/)). When I subsequently tried to remove it with *sudo apt-get remove*, I get ```
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  hot-babe
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 561kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 166962 files and directories currently installed.)
Removing hot-babe ...
dpkg: error processing hot-babe (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 hot-babe
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried the suggestions at [http://ubuntuforums.org/showthread.php?p=2230128](http://ubuntuforums.org/showthread.php?p=2230128), where the same problem is described, but I still can't get rid of the error, which prevents me from installing/removing anything else. I don't care about getting rid of the package; I just want the error to go away so I can install/remove other stuff. Is there any way I can get rid of this error?

Thanks in advance for the help!!!!!

---

### Post by Kateikyoushi on 2007-03-02
Try to reinstall it then remove it.

```
sudo aptitude reinstall hot-babe
```

---

### Post by srunni on 2007-03-02
Never mind, I got the answer. The solution can work for any package that won't remove correctly. By running a system-wide search, I found that some configuration files for the package "hot-babe" were located in /var/lib/dpkg/info . By removing these files, with the command ```
sudo rm /var/lib/dpkg/info/hot-babe*
``` I was able to get the package manager to remove "hot-babe" from the list of installed packages.

---

### Post by fakie_flip on 2007-03-24
I just removed those packages, but my package manager is still broke.

```
chris@ubuntu:~$ sudo find / -iname '*hot-babe*' -exec rm -vi {} \;
rm: remove regular file `/var/lib/dpkg/info/hot-babe.config'? y
removed `/var/lib/dpkg/info/hot-babe.config'
rm: remove regular empty file `/var/lib/dpkg/info/hot-babe.list'? y
removed `/var/lib/dpkg/info/hot-babe.list'
rm: remove regular file `/var/lib/dpkg/info/hot-babe.templates'? y
removed `/var/lib/dpkg/info/hot-babe.templates'
rm: remove regular file `/var/lib/dpkg/info/hot-babe.postinst'? y
removed `/var/lib/dpkg/info/hot-babe.postinst'
rm: remove regular file `/var/lib/dpkg/info/hot-babe.preinst'? y
removed `/var/lib/dpkg/info/hot-babe.preinst'
rm: remove regular file `/var/lib/dpkg/info/hot-babe.postrm'? y
removed `/var/lib/dpkg/info/hot-babe.postrm'
rm: remove regular file `/var/lib/dpkg/info/hot-babe.md5sums'? y
removed `/var/lib/dpkg/info/hot-babe.md5sums'
chris@ubuntu:~$ sudo apt-get install gtetrinet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hot-babe needs to be reinstalled, but I can't find an archive for it.
chris@ubuntu:~$
```

---

### Post by nailbnny on 2007-03-25
Try: sudo dpkg --remove --force-remove-reinstreq hot-babe


-nB

---

### Post by fakie_flip on 2007-03-25
I have tried that already. Here is what happens.

```
chris@ubuntu:~$ sudo dpkg --remove --force-remove-reinstreq hot-babe
Password:
(Reading database ... 171906 files and directories currently installed.)
Removing hot-babe ...
dpkg: error processing hot-babe (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 hot-babe
chris@ubuntu:~$
```

---

### Post by srunni on 2007-03-28
That's exactly what I got. Just run ```
sudo rm /var/lib/dpkg/info/hot-babe*
```

---


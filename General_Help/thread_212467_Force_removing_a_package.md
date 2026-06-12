---
title: "Force removing a package?"
date: 2006-07-09
forum: General Help
---

### Post by The Noble on 2006-07-09
I installed a game (TA Spring) from another thread in this forum.

[http://ubuntuforums.org/showthread.php?t=203448](http://ubuntuforums.org/showthread.php?t=203448)

And it didn't work. I uninstalled everything, but there is some breakage. :( 

I can't remove the package spring-mod-xm for my life. It give's me errors whenever I use any package manager to install or uninstall anything. Is there a way to at least ignore the package so I don't get the error? :rolleyes:

---

### Post by slimdog360 on 2006-07-09
Im going to take a stab, as Ive only just learnt about it(thanks aysiu) and say to use aptitude. Its supposed to get rid of the dependencies. 
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

also try typing
```
sudo apt-get install -f
```
before installing aptitude and see if that helps.

---

### Post by The Noble on 2006-07-09
Eh, I will use aptitue from now on, but it didn't really help with removing the file. I looked at its properties, and it doesn't have any information under installed files (in synaptic. Thus it doesn't know what to uninstall, I presume). Maybe some examples will help. ;)

```

brian@brianlinux:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  spring-mod-xm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4493kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135243 files and directories currently installed.)
Removing spring-mod-xm ...
/var/lib/dpkg/info/spring-mod-xm.postrm: line 23: spring-modupdate: command not found
dpkg: error processing spring-mod-xm (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 spring-mod-xm
E: Sub-process /usr/bin/dpkg returned an error code (1)
brian@brianlinux:~$


```

Sorry for the length, and thank you for the quick reply.

---

### Post by slimdog360 on 2006-07-10
can you check to see if the file
/var/lib/dpkg/info/spring-mod-xm.postrm
is there or not.
Im guessing what has happened is that its uninstalled spring-modupdate package before the spring-mod-xm.postrm file and you probably need the spring-modupdate file to uninstall the other.
Unless someone else has a better idea maybe try reinstalling the game then uninstalling it again.

---

### Post by The Noble on 2006-07-10
It is still there, but I am reading the script and it seems that there may be a command for me to remove the file.

```


...

# summary of how this script can be called:
#        * <postrm> `remove'
#        * <postrm> `purge'
#        * <old-postrm> `upgrade' <new-version>
#        * <new-postrm> `failed-upgrade' <old-version>
#        * <new-postrm> `abort-install'
#        * <new-postrm> `abort-install' <old-version>
#        * <new-postrm> `abort-upgrade' <old-version>
#        * <disappearer's-postrm> `disappear' <r>overwrit>r> <new-version>
# for details, see http://www.debian.org/doc/debian-policy/ or
# the debian-policy package

case "$1" in
       purge|remove|upgrade|failed-upgrade|abort-install|abort-upgrade|disappear)
			spring-modupdate
...

```

EDIT: I ran "sudo sh spring-mod-xm.postrm remove", which should uninstall the mod, but the problem comes up as:

```


brian@brianlinux:/var/lib/dpkg/info$ sudo sh spring-mod-xm.postrm remove
spring-mod-xm.postrm: line 23: spring-modupdate: command not found

```

Thats where the problem is, I think.

By the way, thank you very much for helping. This is why I love Ubuntu and the Community.
:)

---

### Post by slimdog360 on 2006-07-10
this is probably a bit dodgy but first make a backup of the file and store it somewhere safe, then
```
sudo rm /var/lib/dpkg/info/spring-mod-xm.postrm
```
like I said a bit dodgy though, maybe use it as a last resort?

---

### Post by The Noble on 2006-07-10
Beautiful!! It worked well. I created a copy and removed. I apt-get upgraded, and it removed it. I doubt that the files were removed (that it installed), but thats fine by me. Thank you very much. :)

---


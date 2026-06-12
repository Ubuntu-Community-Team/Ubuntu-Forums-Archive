---
title: "firefox broke? missing libmozjs.so"
date: 2007-11-05
forum: General Help
---

### Post by ubiwankanubi on 2007-11-05
I was messing around with apparmor, and tried to make a profile for firefox. but after that, i couldn't get into firefox anymore so I completely removed apparmor. now if i try to start firefox, i get this message:
/usr/lib/firefox/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

i tried locate libjozjs.so but i couldn't find it. SO, I tried to reinstall firefox, but it is still showing this error. How can I get firefox working again?

I'm using ubuntu 7.10 x86_64

---

### Post by mali2297 on 2007-11-05
I ran
```

apt-cache search libmoz

```
That gave this result (among other things):
> 
libmozjs0d - The Mozilla SpiderMonkey JavaScript library


Try therefore
```

sudo apt-get --reinstall install libmozjs0d

```
(You can also use Synaptic.)

---

### Post by ubiwankanubi on 2007-11-05
> **mali2297 said:**
> I ran
```

apt-cache search libmoz

```
That gave this result (among other things):


Try therefore
```

sudo apt-get --reinstall install libmozjs0d

```
(You can also use Synaptic.)


tried that, but still same error:

sudo apt-get --reinstall install libmozjs0d
[sudo] password for ubiwankanubi:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/388kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 122351 files and directories currently installed.)
Preparing to replace libmozjs0d 1.8.1.4-2ubuntu5 (using .../libmozjs0d_1.8.1.4-2ubuntu5_amd64.deb) ...
Unpacking replacement libmozjs0d ...
Setting up libmozjs0d (1.8.1.4-2ubuntu5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubiwankanubi@computer:~$ firefox
/usr/lib/firefox/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

$ locate libmozjs.so
/usr/lib/firefox/libmozjs.so

$ firefox
/usr/lib/firefox/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

any other ideas???

---

### Post by mali2297 on 2007-11-06
Check
```

ls -l /usr/lib/firefox/libmozjs.so

```
It might be a broken link. In any case, remove it (or rename it) and reinstall **libmozjs0d** again. Perhaps it is best to completely remove the package first and then install it:
```

sudo apt-get --purge remove libmozjs0d
sudo apt-get install libmozjs0d

```

---

### Post by ubiwankanubi on 2007-11-06
> **mali2297 said:**
> Check
```

ls -l /usr/lib/firefox/libmozjs.so

```
It might be a broken link. In any case, remove it (or rename it) and reinstall **libmozjs0d** again. Perhaps it is best to completely remove the package first and then install it:
```

sudo apt-get --purge remove libmozjs0d
sudo apt-get install libmozjs0d

```

Tried it, but still no go...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gxine* libmozjs0d*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2322kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127742 files and directories currently installed.)
Removing gxine ...
Purging configuration files for gxine ...
Removing libmozjs0d ...
Purging configuration files for libmozjs0d ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

after that, reinstalled libmozjs0d, but I still get the same error.

~$ locate libmozjs
/usr/share/doc/libmozjs0d
/usr/share/doc/libmozjs0d/MPL.gz
/usr/share/doc/libmozjs0d/changelog.Debian.gz
/usr/share/doc/libmozjs0d/README.Debian
/usr/share/doc/libmozjs0d/copyright
/usr/lib/xulrunner-1.9a8/libmozjs.so
/usr/lib/firefox/libmozjs.so
/usr/lib/libmozjs.so.0d
/var/lib/dpkg/info/libmozjs0d.shlibs
/var/lib/dpkg/info/libmozjs0d.md5sums
/var/lib/dpkg/info/libmozjs0d.postrm
/var/lib/dpkg/info/libmozjs0d.postinst
/var/lib/dpkg/info/libmozjs0d.list
/var/cache/apt/archives/libmozjs0d_1.8.1.4-2ubuntu5_amd64.deb
maybe this helps?

---

### Post by mali2297 on 2007-11-06
Did you also check
```

ls -l /usr/lib/firefox/libmozjs.so

```
?

---

### Post by mali2297 on 2007-11-06
You can also try with a new .mozilla folder:
```

mv ~/.mozilla ~/mozilla_backup
firefox

```

> 
I was messing around with apparmor, and tried to make a profile for firefox. but after that, i couldn't get into firefox anymore so I completely removed apparmor.

Make sure that you really did **completely** remove AppArmor and didn't leave any configuration files.

---

### Post by ubiwankanubi on 2007-11-06
ok, i went to synaptic and did "completely remove" apparmor then firefox works again! Thanks!

---


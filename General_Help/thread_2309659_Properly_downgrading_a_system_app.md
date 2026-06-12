---
title: "Properly downgrading a system app"
date: 2016-01-12
forum: General Help
---

### Post by DigiAngel on 2016-01-12
Topic says it...I've never had the need to do this until now.  I looked at the forums here and elsewhere but didn't really find an answer.  From my apt-history:

```
Upgrade: libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), libgnutls26:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4)
```

This has broken a few things and I'd like to downgrade.  It looks like I need libgnutls-openssl27:amd64 2.12.23-12ubuntu2.3 and libgnutls26:amd64 2.12.23-12ubuntu2.3.  Just doing an:

```
apt-get remove libgnutls26 libgnutls-openssl27
```

threatens to remove all manner of things, conversely:

```
dpkg -r libgnutls26 libgnutls-openssl27
```

errors out.  So...how does one actually downgrade a system package?  Thank you.

---

### Post by DigiAngel on 2016-01-12
So after mucking around online and not finding any complete information here goes:

```
sudo apt-get udpate
```
then check ```
/var/log/apt/history
``` to determine package that got upgrade

check if available in repo:
```
apt-cache showpkg package
```

if not available in repository:
```
cd /var/cache/apt/archives
sudo dpkg -i --force-downgrade package.deb
sudo echo “package hold” | sudo dpkg -–set-selections
```

if available in repository:

```
apt-cache showpkg packagename
sudo apt-get install packagename=version
sudo echo “package hold” | sudo dpkg -–set-selections
```

once issue is fixed use this to upgrade like normal
```
sudo echo “package install” | sudo dpkg -–set-selections
```

Example session (and by example I mean just what I did)
```
sudo apt-get update
tail /var/log/apt/history.log

Start-Date: 2016-01-11  06:34:55
Commandline: apt-get dist-upgrade
Upgrade: libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), libgnutls26:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4)
End-Date: 2016-01-11  06:35:02

cd /var/cache/apt/archives/
sudo dpkg -i --force-downgrade libgnu*2.3*
sudo echo "libgnutls26 hold" | sudo dpkg --set-selections
sudo echo "libgnutls-openssl27 hold" | sudo dpkg --set-selections
```

---

### Post by ian-weisser on 2016-01-12
Yes, that's the right way.
Well done!

Future readers, be aware when using --force-downgrade that dpkg does not do dependency checking, and will happily downgrade to a package that breaks dependencies. Breaking the wrong dependencies can make your system unbootable and really ruin your day. The dpkg man page has a big warning about it.

---

### Post by Kaon_ on 2016-02-17
Hey, great guide but I am having the same issue and I need to downgrade the libgnutls packages to v 2.3 but its not working. The packages are not in the cache.

Any help would be appreciated...

```
:/var/cache/apt/archives# dpkg -i --force-downgrade libgnutls-openssl27.debdpkg: error processing archive libgnutls-openssl27.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libgnutls-openssl27.deb

```


These are the packages that I am trying to downgrade:

```
Upgrade: libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), libgnutls26:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), libgnutls-dev:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), libgnutlsxx27:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4)
```

System: Linux 3.13.0-76-generic #120-Ubuntu SMP

---

### Post by oldos2er on 2016-02-17
Kaon_, please start a new thread. "Hijacking" solved threads means fewer people are going to be aware of your question.

---


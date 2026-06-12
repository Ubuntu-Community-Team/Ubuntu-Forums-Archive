---
title: "can't get 18.04 to work with local repository"
date: 2018-10-06
forum: General Help
---

### Post by gobo7 on 2018-10-06
i've been struggling for a week now trying to get a local repository to update a new
18.04 install.  i'm not new to local repos, i've had one since 12.04.  but nothing
i've learned over the years has been of any help.  i did skip 16.04, so i've
missed something.  i'll gladly study anything, if someone can point me to notes
for 18.04.

my update
```

apt-get --allow-unauthenticated update

```

right now i'm leaning to packages being ignored.  but i have no idea why.
```

root@t400:/etc/apt# apt-get update --allow-unauthenticated        
Get:1 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:1 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:2 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:3 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Get:2 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:3 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Get:4 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic/main i386 Packages [1,007 kB]
Ign:4 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic/main i386 Packages
Get:5 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1,019 kB]
Ign:5 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic/main amd64 Packages
Get:6 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic/main Translation-en [516 kB]
Ign:6 file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic/main Translation-en
...

```

sources.list
```

#deb cdrom:[Kubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725)]/ bionic main multiverse restricted universe
#deb http://archive.ubuntu.com/ubuntu/ bionic main restricted universe
#deb http://security.ubuntu.com/ubuntu/ bionic-security main restricted universe
#deb http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe

deb file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic main  
deb file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic restricted 
deb file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic universe
deb file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic multiverse

deb file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse
deb file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse

#deb file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
#deb-src file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic main restricted universe multiverse

```

trying to install vim with apt-get install vim returns not available.
can anyone offer a suggestion?  

thanks in advance!

---


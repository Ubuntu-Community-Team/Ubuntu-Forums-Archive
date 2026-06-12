---
title: "Can't install Universal repo on live USB"
date: 2024-03-09
forum: General Help
---

### Post by john163 on 2024-03-09
```
ubuntu@ubuntu:~$ sudo add-apt-repository universe
Adding component(s) 'universe' to all repositories.
Press [ENTER] to continue or Ctrl-c to cancel.
Ign:1 cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy Release
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease                                                               
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                     
Hit:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Reading package lists... Done
W: Skipping acquire of configured file 'universe/binary-amd64/Packages' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/i18n/Translation-en_US' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/i18n/Translation-en' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/Components-amd64.yml' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-48x48.tar' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-64x64.tar' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-64x64@2.tar' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/cnf/Commands-amd64' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)

ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220)]/ jammy restricted main universe
deb http://archive.ubuntu.com/ubuntu/ jammy restricted main universe
deb http://security.ubuntu.com/ubuntu/ jammy-security restricted main universe
deb http://archive.ubuntu.com/ubuntu/ jammy-updates restricted main universe

ubuntu@ubuntu:~$ sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) main universe restricted multiverse"
Repository: 'deb http://archive.ubuntu.com/ubuntu jammy restricted universe multiverse main'
Description:
Archive for codename: jammy components: restricted,universe,multiverse,main
More info: http://archive.ubuntu.com/ubuntu
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Updating existing entry instead of using /etc/apt/sources.list.d/archive_uri-http_archive_ubuntu_com_ubuntu-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list
Ign:1 cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy Release
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease                                                               
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                     
Hit:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Get:7 http://archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages [217 kB]
Get:8 http://archive.ubuntu.com/ubuntu jammy/multiverse Translation-en [112 kB]
Get:9 http://archive.ubuntu.com/ubuntu jammy/multiverse amd64 DEP-11 Metadata [42.1 kB]
Get:10 http://archive.ubuntu.com/ubuntu jammy/multiverse DEP-11 48x48 Icons [42.7 kB]
Get:11 http://archive.ubuntu.com/ubuntu jammy/multiverse DEP-11 64x64 Icons [193 kB]
Get:12 http://archive.ubuntu.com/ubuntu jammy/multiverse DEP-11 64x64@2 Icons [214 B]
Get:13 http://archive.ubuntu.com/ubuntu jammy/multiverse amd64 c-n-f Metadata [8,372 B]
Fetched 615 kB in 1s (732 kB/s)                                       
Reading package lists... Done
W: Skipping acquire of configured file 'universe/binary-amd64/Packages' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/i18n/Translation-en' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/i18n/Translation-en_US' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/Components-amd64.yml' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-48x48.tar' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-64x64.tar' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-64x64@2.tar' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/cnf/Commands-amd64' as repository 'cdrom://Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220) jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)

ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220)]/ jammy restricted main universe
deb http://archive.ubuntu.com/ubuntu/ jammy multiverse restricted universe main
# deb-src http://archive.ubuntu.com/ubuntu jammy restricted universe multiverse main
deb http://security.ubuntu.com/ubuntu/ jammy-security restricted main universe
deb http://archive.ubuntu.com/ubuntu/ jammy-updates restricted main universe
```

I need it to install a package:

```
ubuntu@ubuntu:~$ sudo apt install intel-opencl-icd
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package intel-opencl-icd
```

---

### Post by Bashing-om on 2024-03-09
john163; Hello

1) I do suggest that the cdrom be disabled in software sources as the access is no longer required.
2) run in terminal "sudo apt update" so that the package manager is aware of the change
3) check your source list files to insure that the universe repo is not now duplicated.

Now what shows:
```

sudo apt update

```

-maybe yes-

---

### Post by C.S.Cameron on 2024-03-12
If you want a persistent install of Universal to a USB it must be either a Persistent Live USB or a Full Install USB. You can not save stuff on a Live only USB.

---

### Post by Bashing-om on 2024-03-12
Ouch on me :D
^^

> 
repo on live USB


-take some time and comprehend what you read-

---


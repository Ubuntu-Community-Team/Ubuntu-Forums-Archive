---
title: "Updates Failed"
date: 2024-07-08
forum: General Help
---

### Post by dfpd62 on 2024-07-08
Hi,
Ubuntu 16.04lts has encountered an error that I cant seem to fix
It reads" Error opening the cache" (E:Encountered a section with no package: header, E:problem with mergelist/var/lib/apt/lists/gb.archive.com_ubuntu_dists_xenial_main_binary_i386_Packages, E:The package lists could not be opened or parsed"
I tried running apt-get upgrade which failed after it was 20% through (35 hours later) 

Ign:186 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/restricted Translation-en
Ign:187 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/restricted i386 DEP-11 Metadata
Reading package lists... Error!
W: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-i386/Packages)  Connection failed [IP: 91.189.91.81 80]
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages)  Connection failed [IP: 185.125.190.39 80]
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-i386/Packages)  Connection failed [IP: 185.125.190.81 80]
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/main/binary-i386/Packages)  Connection failed [IP: 185.125.190.82 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Any help appreicated . D

---

### Post by currentshaft on 2024-07-08
Ubuntu 16 is over 8 years old. It is time to upgrade your system.

---

### Post by Rubi1200 on 2024-07-09
Unless you have ESM or Pro enabled, Xenial support ended in April 2021.

Backup all important data and install a more recent LTS version.

I recommend 22.04 or at least wait for the first point release of 24.04 in August.

---

### Post by dfpd62 on 2024-07-09
Thanks for that, can you recommend a distro that will work well with my old Acer Travelmate P253e, Intel r960 processor and 4gb Ram?

Its mostly used by my Grandaughter to do her Homework....

---

### Post by ActionParsnip on 2024-07-09
CPU is a B960 according to the Acer site. It's a 64bit 2.2Ghz 2 cores (no HT) CPU. Should be OK with Xubuntu without any problems, IMHO.

---

### Post by Frogs Hair on 2024-07-09
Lubuntu is probably the lightest Ubuntu flavor , but is no longer focused on low spec hardware. Ubuntu flavors are supported for three years. It has a different desktop environment, but the same office program.

[https://lubuntu.me/noble-released/](https://lubuntu.me/noble-released/)

[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

---

### Post by Rubi1200 on 2024-07-09
> **dfpd62 said:**
> Thanks for that, can you recommend a distro that will work well with my old Acer Travelmate P253e, Intel r960 processor and 4gb Ram?

Its mostly used by my Grandaughter to do her Homework....
That's really cool :-)

I tried to get my kids into Linux but they were having none of it.

Bodhi Linux, which is based on Debian/Ubuntu, works really well on older hardware or low-spec machines.
[https://www.bodhilinux.com/](https://www.bodhilinux.com/)

---


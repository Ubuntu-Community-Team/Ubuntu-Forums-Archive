---
title: "Problem with apt-get update and ftp.nerim.net"
date: 2005-07-30
forum: General Help
---

### Post by jbla00 on 2005-07-30
When I have 

```
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main
deb ftp://ftp.nerim.net/debian-marillat/ stable main

```

in my sources.list I get the following errors when issuing "apt-get update"

```
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz  MD5Sum mismatch
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz  MD5Sum mismatch
Reading package lists... Done
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

What is going wrong here?

I've read in an other thread that one should use the "hoary-extras" from the backports repository in stead. Can I just replace the ftp.nerim.net lines with

```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

to my sources.list?

What about the apps that I have installed from the ftp.nerim.net repository? Are they available from the hoary-extras repository? Will they automatically be updated (if needed)? If not, will I need to uninstall the apps I've got from ftp.nerim.net and reinstall them from hoary-extras?

Jesper

---

### Post by DJ_Max on 2005-07-30
First, you shouldn't use Debian repositories, such as [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/). They're meant for Debian, not Ubuntu.

The Hoary backports should have everything you need. Depending on what apps you're installed from the nerim.net FTP site, you should uninstall them, and install the official ones from the backports.

---

### Post by jbla00 on 2005-08-04
Is there any way which packages I have installed from ftp.nerim.net?

I know I installed mplayer, but other packages might have been installed with it.

Jesper

---

### Post by tomchuk on 2005-08-04
There's probably a cleaner, more efficient way to do this but...
```
apt-cache policy $(dpkg --get-selections| awk '{print $1}') | grep -B5 ftp.nerim.net | grep '^[[:alnum:]]' | cut -d: -f1
```
That should give you a list of installed packages from nerim.net.

---

### Post by jbla00 on 2005-08-08
Thanks a bunch

Jesper

---


---
title: "weird warning in Synaptic Package Manager"
date: 2005-10-26
forum: General Help
---

### Post by autonomy on 2005-10-26
I've been getting the following weird message after doing something that I can't remember and installing a lot of applications:> The following problems were found on your system:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
I can only hope this isn't a problem. For now, it's just annoying because it keeps popping up on the screen.

---

### Post by Psquared on 2005-10-26
In a terminal clean your apt-get cache, then run sudo apt-get update; or you can rerun synaptic and click reload. Also make sure your internet connection is up and running.

---

### Post by autonomy on 2005-10-26
The second option worked. Thanks. I didn't try the first.

---

### Post by tanmay80 on 2005-10-27
I reopened Synaptic Manager and reload,

Still get the following errors

[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.165 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.165 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.165 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.165 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) 404 Not Found [IP: 130.239.18.165 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:) 404 Not Found [IP: 130.239.18.165 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:) 404 Not Found [IP: 130.239.18.165 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) 404 Not Found [IP: 130.239.18.165 80]

How do I refresh cache of apt-get?

thanks in advance

---

### Post by Nomad64 on 2005-10-27
Remove the "us" part of the DNS address from your sources.list file. For some reason, the country code(s) mess up the DNS resolution.

```
sudo gedit /etc/apt/sources.list
```

Find the instance of "http://us.archive.ubuntu.com..." and remove the "us." part of the line. Save the file, and then run 
```
sudo apt-get update
```

The errors should be gone. There was a thread in the forums with a fixed version of the sources.list file, I will find the link and post it here for ya.

EDIT: Ok, I couldn't find the thread I had in mind; however, I got this link: [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html). If you use the bottom example of the sources.list, just copy/paste into your sources.list file, and all will be dandy. Just remember, this won't give you access to the extra stuff (win32codecs, java, etc.) For that, you have to add a few extra repositories. There are several you can add, but I use cyberfunk.org for mine. Just add the following line into your sources.list file:
```
deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main
```

---


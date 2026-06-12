---
title: "importing files from encfs"
date: 2020-09-12
forum: General Help
---

### Post by gemalo on 2020-09-12
All,

Recently I have updated my system to Kubuntu 20.04, from 18.10.  I have my operating system and most used applications on a dedicated nvme drive, and I have kept all of my data on another independent disk drive in a large folder encrypted with gnome-encfs-manager. Unfortunately, I believe that encfs is now depreciated in 20.04, and I'm not sure how to access my files.  To be clear, I was able to access everything prior to the upgrade.

What I have:

1. The physical hard drive, which I can mount and access up to the directory where the files are located, and where I get a permission denied error.  I know that the data on the drive is there; I'm just unsure of the best way to access it.
2. A computer that operates Kubuntu 20.04, but cannot install gnome-encfs-manager
3. A usb drive with 18.04 that I can boot a live environment, and install gnome-encfs-manager, however once I get there I am lost. Again, I can see the directory but get a permission denied error. (Maybe something to do with the mount point but I really don't know)
4. The passwords required for the directories in encfs
5. A basic, limited understanding of Kubuntu. Everything in layman's terms please.  I'll need to be walked through each step, ok with using terminal.

In all reality, if I can get access to the files I will unencrypt them until I find a better solution.  At this point I am just concerned about restoring access of my files!

Thank you

---

### Post by scorp123 on 2020-09-13
> **gemalo said:**
>  Recently I have updated my system to Kubuntu 20.04, from 18.10.  I have my operating system and most used applications on a dedicated nvme drive, and I have kept all of my data on another independent disk drive in a large folder encrypted with gnome-encfs-manager. Unfortunately, I believe that encfs is now depreciated in 20.04, and I'm not sure how to access my files. 

Take a look at **Sirikali**.
It definitely is in the "Universe" repositories for Ubuntu 20.04 

```

#: ~> apt show sirikali

Package: sirikali
Version: 1.4.2-2
Priority: extra
Section: universe/admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: David Steele <steele@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 2&#8217;417 kB
Depends: libc6 (>= 2.14), libgcc-s1 (>= 3.0), libgcrypt20 (>= 1.8.0), libqt5core5a (>= 5.12.2), libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2), libqt5network5 (>= 5.0.2), libqt5widgets5 (>= 5.0.2), libsecret-1-0 (>= 0.7), libstdc++6 (>= 9)
Recommends: cryfs
Suggests: encfs, gocryptfs, ecryptfs-utils, sshfs
Homepage: http://mhogomchungu.github.io/sirikali
Download-Size: 691 kB
APT-Sources: http://ch.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: Manage user encrypted volumes
 Sirikali provides a Qt/C++ GUI front end to cryfs,gocryptfs,securefs and encfs,
 allowing the user to create, mount, and unmount encrypted volumes.

```

As indicated by the package's info, the project's homepage is here:
[URL="https://mhogomchungu.github.io/sirikali/"]https://mhogomchungu.github.io/sirikali/
[/URL]

Sirikali should be able to read EncFS-encrypted stuff (it was in my case) and you can also use it to move the data over into a more modern encryption format. Just let Sirikali mount your old EncFS folder and drag & drop the files into their new location. Done.

---

### Post by gemalo on 2020-09-13
Thanks scorp, problem solved.  Fixed!!

---


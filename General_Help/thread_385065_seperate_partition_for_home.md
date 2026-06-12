---
title: "seperate partition for /home"
date: 2007-03-15
forum: General Help
---

### Post by logesh on 2007-03-15
In preparation for Ubuntu 7, I would like to further partition my linux disk and put the /home folder in its own volume.

How do I do that from the command-line?

If it works, I thought I may want to further partition and install another distro (Opensuse?).  Can grub reflect more than 2 OSs?  I don't suppose both linuxes (linices?) can reference the same home folder.

---

### Post by bollix47 on 2007-03-15
See if anything [_here_]("http://www.psychocats.net/ubuntu/separatehome") helps.

---

### Post by Kateikyoushi on 2007-03-15
You can share the home partition between distributions and grub can deal with more than 2 OS as well.

---

### Post by DavidTangye on 2007-03-15
Its generally a bad idea to share /home between different linux installs, because the configuration data for applications in hidden directories, ie .mozilla etc, might not be compatible if the apps in the different installs are of differing versions. This could lead to corruptions, the therefore such outcomes like some apps not running properly or at all.

Its better to have separate /homes for each installation, and place your files that you want to share in a common area. For example, make a shared-common partition "homedocs" and mount it at /mnt/homedocs, and within this create a subdirectory for each user, eg /mnt/homedocs/fred. At each /home/fred fred can create a link to it, eg
ln -s /mnt/homedocs/fred $HOME/MyDocuments

---


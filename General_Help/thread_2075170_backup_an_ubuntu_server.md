---
title: "backup an ubuntu server"
date: 2012-10-23
forum: General Help
---

### Post by hhaydoura on 2012-10-23
hey guys, I want to backup the server from my client pc, well i want to do that using rsync, does anyone know any keys to help doing this? :)

---

### Post by Lars Noodén on 2012-10-23
Here are three sources covering about the same thing from slightly different angles:

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync)

It's probably enough to get just the data and the configuration files.

---

### Post by Lars Noodén on 2012-10-23
Aside from the configuration files there is not so much of a need to back up the system itself.  You can get a list of what you have installed and uninstalled using [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html)

```

dpkg --get-selections > my_packages.txt

```

Later you can restore on a new machine.

```

sudo dpkg --clear-selections
sudo dpkg --set-selections < my_packages.txt
sudo apt-get dselect-upgrade

```

---


---
title: "Autoremove,update,etc"
date: 2017-08-03
forum: General Help
---

### Post by raleigh3 on 2017-08-03
sudo -S apt -y autoremove
 sudo -S apt -y update
 sudo -S apt -y full-upgrade

I have been curious about something for a while.

When I run these, sometimes it frees up 1 Mb of free space.

My entire space used is 35 Mb.

What is it doing when it frees up that space ?

Why is that not done when programs are installed/un-installed ?

Thanks. :-)

---

### Post by vocx on 2017-08-03
> **raleigh3 said:**
> sudo -S apt -y autoremove
 sudo -S apt -y update
 sudo -S apt -y full-upgrade

I have been curious about something for a while.

When I run these, sometimes it frees up 1 Mb of free space.

My entire space used is 35 Mb.

What is it doing when it frees up that space ?

Why is that not done when programs are installed/un-installed ?

Thanks. :-)

You can read the manual of "apt" and "apt-get" to know what the commands do.

The option "update" does not delete anything. It downloads an updated list of packages, so that the system knows about new and updated packages.

The option "full-upgrade" performs an "upgrade", meaning it downloads new versions of currently installed packages. The "full-upgrade" option may remove currently installed packages if this is needed to upgrade the system as a whole. Probably this means it will prepare the system for when you want to transition from one version of Ubuntu to the next one.

The option "autoremove" removes packages that were installed as dependencies of another package but are no longer needed. When you update your packages sometimes they change their dependencies, so the "autoremove" option allows you to remove the old dependencies that are not needed anymore. When you install new Linux kernels you often see this message, because your system will have the new kernel, and two previous versions. So the "autoremove" option deletes the second oldest one so you keep only two, the newest one, and one older.

What does it mean "remove"? Well, it simply removes the files that came with the package. You can list all the files that came with a package.
```

dpkg -L vim

```

Why is this not done when installing and uninstalling? Why would it? Linux systems usually give you fine control on the installation and deinstallation of programs. If things were too automated it would cause problems with the power users that want to install specific packages.

The system usually keeps all the packages that you installed in your system, in case you need to reinstall or reconfigure a package.
```

ls -lah /var/cache/apt/archives

```

Imagine if you install a heavy package and then you delete it at the end. Maybe you had to download 500 MB of data, and don't have access to the Internet. So what do you do? Keeping the packages there is no problem, unless it really takes a lot of space in your hard drive. Of course you can clean up these packages with "sudo apt clean".

---


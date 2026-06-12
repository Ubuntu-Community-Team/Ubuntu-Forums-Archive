---
title: "Lubuntu 18.04: sudo apt-get dist-upgrade wants to remove lubuntu-desktop"
date: 2020-06-15
forum: General Help
---

### Post by ardouronerous on 2020-06-15
I'm on Lubuntu 18.04.4, and I'm not planning on updating to Lubuntu 20.04 until at least next year. It all started this morning. I've set update-manager to run on  startup and it gave me this "Not all updates can be installed" message,  so I checked in with Synaptic Package Manager and I got this message  when I checked for updates, wanting to remove lubuntu-desktop and  lubuntu-gtk-desktop and other stuff.

Then I ran sudo apt-get dist-upgrade, this is the result:

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  sbsigntool secureboot-db
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  fwupd-signed fwupdate-signed lubuntu-desktop lubuntu-gtk-desktop
The following packages will be upgraded:
  fwupd
1 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 2,481 kB of archives.
After this operation, 123 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
```

 
What's going on?

---

### Post by Dennis N on 2020-06-15
We're advised by Lubuntu team not to upgrade Lubuntu 18.04 except by doing a new install. This was in the release notes for 18.10 if I'm not mistaken. You can check. It's because of the change from LXDE to LXQt.

---

### Post by ardouronerous on 2020-06-15
> **Dennis N said:**
> We're advised by Lubuntu team not to upgrade Lubuntu 18.04 except by doing a new install. This was in the release notes for 18.10 if I'm not mistaken. You can check. It's because of the change from LXDE to LXQt.

Except, I'm not upgrading to Lubuntu 20.04, I'm updating the software on 18.04, and this is the result.

---

### Post by Bashing-om on 2020-06-15
ardouronerous; Hello -

Our developers are hard at work on fwupd:
[https://bugs.launchpad.net/ubuntu/+source/fwupd-signed/+bug/1883595](https://bugs.launchpad.net/ubuntu/+source/fwupd-signed/+bug/1883595)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Dennis N on 2020-06-16
Well, keep that advice in mind when you do upgrade. It's hard to tell why lubuntu-desktop is being removed, but dist-upgrade can remove packages in some cases (check man page description). In any case, it's a metapackage, and it's removal does not remove any applications, so it's safe to remove. lubuntu-gtk-desktop is probably another metapackage, but if you want to confirm that, check with: 
apt show lubuntu-gtk-desktop.
It should tell you its a metapackage.

---

### Post by ardouronerous on 2020-06-16
> **Dennis N said:**
> Well, keep that advice in mind when you do upgrade.

Thanks for the advice. In my experience starting with Lubuntu 12.04, upgrading the system using the updater usually fails, so I also opt for a clean install.

> **Dennis N said:**
> It's hard to tell why lubuntu-desktop is being removed, but  dist-upgrade can remove packages in some cases (check man page  description). In any case, it's a metapackage, and it's removal does not  remove any applications, so it's safe to remove. lubuntu-gtk-desktop is  probably another metapackage, but if you want to confirm that, check  with: 
apt show lubuntu-gtk-desktop.
It should tell you its a metapackage.

Thanks for this information, so are all metapackages are safe to remove then?

Here's the result of sudo apt-get dist-upgrade:

```
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  sbsigntool secureboot-db
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  fwupd-signed fwupdate-signed lubuntu-desktop lubuntu-gtk-desktop
The following packages will be upgraded:
  fwupd
1 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 2,481 kB of archives.
After this operation, 123 kB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 fwupd amd64 1.2.10-1ubuntu2~ubuntu18.04.5 [2,481 kB]
Fetched 2,481 kB in 7s (350 kB/s)                                              
(Reading database ... 179345 files and directories currently installed.)
Removing lubuntu-desktop (0.94.1) ...
Removing lubun~$ sudo tu-gtk-desktop (0.94.1) ...
Removing fwupdate-signed (12-7~ubuntu18.04.3) ...
Removing fwupd-signed (1.10~ubuntu18.04.3+1.2.10-1ubuntu2~ubuntu18.04.3) ...
(Reading database ... 179332 files and directories currently installed.)
Preparing to unpack .../fwupd_1.2.10-1ubuntu2~ubuntu18.04.5_amd64.deb ...
Unpacking fwupd (1.2.10-1ubuntu2~ubuntu18.04.5) over (1.2.10-1ubuntu2~ubuntu18.04.3) ...
Setting up fwupd (1.2.10-1ubuntu2~ubuntu18.04.5) ...
fwupd-offline-update.service is a disabled or a static unit not running, not starting it.
fwupd.service is a disabled or a static unit not running, not starting it.
Processing triggers for dbus (1.12.2-1ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  sbsigntool secureboot-db
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 394 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 179331 files and directories currently installed.)
Removing secureboot-db (1.4~ubuntu0.18.04.1) ...
Removing sbsigntool (0.6-3.2ubuntu2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
```

So far so good as far as I can tell.

---


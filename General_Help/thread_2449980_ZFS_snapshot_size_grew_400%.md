---
title: "ZFS snapshot size grew 400%"
date: 2020-09-05
forum: General Help
---

### Post by danik56 on 2020-09-05
I take a weekly ZFS snapshot of the system root file system, and the size has always been near 15GB since upgrading to the current Ubuntu version.
The last snapshot grew in size to 70GB and I can see why.  No installs or upgrades were made since the previous snapshot.
How can I find what is causing the size increase ?

---

### Post by scorp123 on 2020-09-05
> **danik56 said:**
>  How can I find what is causing the size increase ?

Do a "sudo zfs diff". .... Example:

First I want to see what snapshots I have and how big they are:
```
zfs list -t snapshot -o creation,space -s creation
```

And now I want to know why on my system e.g. "/usr/local" has grown in size.
If I use "sudo zfs diff" with only 1 x snapshot argument then that snapshot gets compared to the current situation:

```
sudo zfs diff rpool/ROOT/ubuntu_xx1234/usr/local@autozsys_dndo4m
M       /usr/local/share/ca-certificates

```

So "M" means "modified" here. And there's a size difference because "/usr/local/share/ca-certificates" has changed in size since that snapshot above was taken.

You can also compare 2 x snapshots with each other:

```
 sudo zfs diff rpool/USERDATA/root_r73p5r@autozsys_dndo4m  rpool/USERDATA/root_r73p5r@autozsys_wwolyg

M       /root/.cache
+       /root/.inputrc
+       /root/.vimrc
+       /root/.anydesk
+       /root/.anydesk/.anydesk.trace
+       /root/.anydesk/anydesk.trace
+       /root/.anydesk/incoming
+       /root/.ssh
+       /root/.ssh/id_rsa
+       /root/.ssh/id_rsa.pub
M       /root/
M       /root/.bashrc
M       /root/.profile
+       /root/.bash_history
+       /root/.config
+       /root/.config/VirtualBox
+       /root/.config/VirtualBox/xpti.dat
+       /root/.config/VirtualBox/compreg.dat
+       /root/.config/VirtualBox/VBoxSVC.log
+       /root/.tmux.conf
+       /root/.ssh/authorized_keys
+       /root/.viminfo
+       /root/.ssh/known_hosts
+       /root/.cache/motd.legal-displayed

```

So here I can see that files were modified ("M"), deleted ("-") or added ("+") and that thus I get the size difference between the snapshots that the command "zfs list -t snapshot -o creation,space -s creation" shows on my system.

---


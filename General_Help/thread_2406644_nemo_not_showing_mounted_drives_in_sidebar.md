---
title: "nemo not showing mounted drives in sidebar"
date: 2018-11-23
forum: General Help
---

### Post by box02-0 on 2018-11-23
Hi.

I am testing Ubuntu 18.04 using Nemo 3.6.5 and mounted drives are NOT showing in the sidebar. This worked fine in Ubuntu 16.04 which I have just upgraded from.

I tried going to EXTENSIONS in GNome Tweaks and toggled 'ubuntu appindicator' and 'ubuntu dock' Off and then back ON to avail.I also tried toggling OFF/ON for 'Show Icons' and 'Mounted Volumes' on DESKTOP to no avail.

Interesting to note that the TRASH icon is not displayed in the sidebar as well, rather as a Desktop Icon.

In DISKS, the Mount options are: nosuid,nodev,nofail,x-gvfs-show  (Session Defaults are ON).

Any thoughts would be greatly appreciated.

Thanks,
M....

---

### Post by ajgreeny on 2018-11-23
I assume files (ie nautilus) is still installed in your 18.04?

Do mounted volumes show in that?

If so, I wonder if your upgrade instead of a clean install was less than successful; I've never upgraded and always clean install from one version of LTS to the next LTS as too many times I have read about upgrade problems in this forum.

---

### Post by again? on 2018-11-23
I use nemo and mounted drives show as they did in 16.04.
By default all show but can be changed in disks by turning off user session defaults.
Fresh install 18.04.

Check your /etc/fstab file.
Disks writes changes to mount options here.

Run... 
```
sudo apt update && sudo apt upgrade
```
and check for errors.

---

### Post by box02-0 on 2018-11-27
Hi.

Mounted drives did not show in sidebar launcher for Nemo or Nautilis.

Okay,  I have solved my problem - All works fine with Unity Desktop  Environment. Mounted volumes and Trash icon now working AOK. I prefer  Unity over Gnome so this works well for me.

I have many, many,  apps, each with customized menus, so I chose to Update to 18.04 vs a  clean install. No doubt a clean install is the smarter way to go, but  thie Update was way quicker and seems to be working fine.

Thanks to all for your input. Now I just have to figure out how to mark this post as Solved.

M....

---


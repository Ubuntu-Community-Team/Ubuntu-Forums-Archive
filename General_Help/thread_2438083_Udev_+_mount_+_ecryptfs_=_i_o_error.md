---
title: "Udev + mount + ecryptfs = i o error"
date: 2020-03-05
forum: General Help
---

### Post by loiren on 2020-03-05
[COLOR=#000000][FONT=Arial]Ubuntu 18. There is a rule in udev - if the serial number matches, run the script. In the script, user verification is a mount rule, the mount itself, and the ecryptfs container mount. Found a note to mount udev you need to register /etc/systemd/system/systemd-udevd.service MountFlags=shared .I insert a USB flash drive the script works out the container is mounted, but when trying to open any file in the container even with root-an access error.If you manually run the script, everything works.When auto-mounting:udevadm monitor/devices/virtual/bdi/ecryptfs-5 (bdi)I. e. I understand it as private namespaces.How i can do this?[/FONT][/COLOR]

---


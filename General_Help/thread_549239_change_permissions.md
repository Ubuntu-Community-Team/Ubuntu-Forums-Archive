---
title: "change permissions"
date: 2007-09-12
forum: General Help
---

### Post by DrEmpire on 2007-09-12
i need need to change permission for 2 hard drives to be able to write to them from ubuntu, they both used for windows(my documents)they are both ntfs, but i thought it was possible to use these drives on ubuntu now,   how change permission of the drives so i can write and read

---

### Post by Harpoon on 2007-09-12
apt-get ntfs-3g and ntfs-config, then run sudo ntfs-config and follow the gui

---

### Post by DrEmpire on 2007-09-12
what does this mean? ( WARNING **: Error : This programm need to be run as root)

---

### Post by Maestro23 on 2007-09-12
> **DrEmpire said:**
> what does this mean? ( WARNING **: Error : This programm need to be run as root)

Try using "sudo" in front of your commands.

---


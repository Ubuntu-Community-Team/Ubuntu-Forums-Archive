---
title: "weird folder permission thing"
date: 2004-10-28
forum: General Help
---

### Post by geoff on 2004-10-28
i just installed warthog, and it seems very nice, congratulations!  i am, however, having a somewhat peculair scenario.  here's my hard drive setup

hda1: windows 2000, ntfs
hda5: ubuntu, reiserfs
hda6: nothing, planning to do a lfs at some point
hda7: swap
hda8: files with music, etc, formatted as fat32, and is mounted as /win2

i tried to open some folders on /win2, and the folders appeared as empty files.  opened nautilus up as root, and it sees the folders and all the juicy files inside.  when i go to change the permission within nautilus by using the checkboxes, they go right back to where they were.  if i try to change the ownership of the folder, it won't let me.  even chmod on the cli is not working.  this is very frustrating for me, seeing as how i am now sitting in silence.  any help would be greatly appreciated.

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=geoff]i just installed warthog, and it seems very nice, congratulations!  i am, however, having a somewhat peculair scenario.  here's my hard drive setup

hda1: windows 2000, ntfs
hda5: ubuntu, reiserfs
hda6: nothing, planning to do a lfs at some point
hda7: swap
hda8: files with music, etc, formatted as fat32, and is mounted as /win2

i tried to open some folders on /win2, and the folders appeared as empty files.  opened nautilus up as root, and it sees the folders and all the juicy files inside.  when i go to change the permission within nautilus by using the checkboxes, they go right back to where they were.  if i try to change the ownership of the folder, it won't let me.  even chmod on the cli is not working.  this is very frustrating for me, seeing as how i am now sitting in silence.  any help would be greatly appreciated.[/QUOTE]


You have to change the permissions when the drive is mounted.  Edit the /etc/fstab and change the umask for the drive.

---

### Post by im_ka on 2004-10-28
have you tried editing /etc/fstab?
```
sudo gedit /etc/fstab
```
add "user, rw" to the options. this will -obviously- enable users to read/write the partition.

hope this helps

---

### Post by jdong on 2004-10-29
[QUOTE=im_ka]have you tried editing /etc/fstab?
```
sudo gedit /etc/fstab
```
add "user, rw" to the options. this will -obviously- enable users to read/write the partition.

hope this helps[/QUOTE]
**WRONG**.

User means that users can *mount* the partition, has nothing to do with permissions. Use **umask=0**

---


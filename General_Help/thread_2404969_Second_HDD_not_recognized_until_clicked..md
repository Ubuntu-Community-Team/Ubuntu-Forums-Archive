---
title: "Second HDD not recognized until clicked."
date: 2018-10-30
forum: General Help
---

### Post by gottaslay on 2018-10-30
I cant download anything on the hard drive unless i go to Files and click on the hard drive icon there.

---

### Post by Bashing-om on 2018-10-30
gottaslay; Hello -

The system is not going to second guess what you want to do.
If you want a drive to be available upon booting up, ya got to tell the system so.

One way to do so is explicitly declare the mount.
That directive is in the /etc/fstab file.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

for some pointers on what you might want to do.

I personally only mount my data drives as "on demand"; As I want to be fully aware of what ever might happen.

[INDENT][INDENT]tell me, what to do
[/INDENT][/INDENT]

---


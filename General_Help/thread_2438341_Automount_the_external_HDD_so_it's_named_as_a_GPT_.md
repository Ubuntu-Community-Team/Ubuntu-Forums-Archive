---
title: "Automount the external HDD so it's named as a GPT partition label"
date: 2020-03-10
forum: General Help
---

### Post by FarJumper on 2020-03-10
Trying to understand how to make Ubuntu Gnome to automount the external HDD so it's mounting point is named after a GPT partition label. I'm not sure which daemon does the work for mounting plugged medias to /media/<user> directory, but it looks like it uses the Filesystem Partition Label first if available, then it fails back to using the UUID of the partition. Wondering if that's possible to configure so it's:
  1) Filesystem Label, then 
  2) GPT Partition Label, then 
  3) Filesystem's UUID. 

Another question, why it's not configured like this by default? What's the point having the GPT label if it's not beind used in the logic of acquiring the human-readable name of the volume?

---

### Post by TheFu on 2020-03-10
There are multiple tools that can "automount" storage.  IMHO, the worst one to use is the one that happens automatically and wants to put storage under /media/ .

The other two methods are either **autofs** or **systemd-automount**. Both of these methods let you specify exactly where and how you want storage mounted.  PERIOD.  However, I would stay away from using /media/, since some other mount tool is already mis-managing that area.
Here's an example for using the systemd-automount method: 
[https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156)  that post is about network storage, but it works using **LABEL=** mounts instead of network paths. You'll need to manually ensure the LABELs are unique.  Just get the file system type correct in the fstab.

---


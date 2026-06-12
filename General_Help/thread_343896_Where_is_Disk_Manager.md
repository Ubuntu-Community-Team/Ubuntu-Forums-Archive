---
title: "Where is Disk Manager?"
date: 2007-01-22
forum: General Help
---

### Post by updownleftright on 2007-01-22
I'm trying to mount my windows XP NTFS partitions as drives in Ubuntu 6.10, and all the tutorials (online and the ubuntu help docs) all mention opening "System/Administration//Disk Manager" or "System/Administration/Disks", but I don't have anything like this in my admin menu. I've even tried opening the menu manager and seeing if there is a Disk Manager button that is just hidden, but it's not there either.

If I look in the Device Manager I can see the other Hard Drive. The setup is a 160gb drive with XP on and about 5 partitions, and a 20gb slave drive with ubuntu on it (in 3 partitions I think, whatever it defaulted to)

Any idea why this is?

---

### Post by updownleftright on 2007-01-22
Sorry, I've just looked a bit harder on the forum and it seems that gnome no longer includes Disk Manager, and I should pysdm instead.

Perhaps someone should update the ubuntu help files so they don't tell people to open apps that no longer exist?

Just a suggestion from a clueless noob, but seeing as Ubuntu is supposed to be the user friendly face of Linux, little things like that matter! :)

---

### Post by Josh1 on 2007-01-22
Hi there,

If you want to mount the Windows NTFS, simply open up Terminal (Applications -> Accessories -> Terminal) and type in the following:

```

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0777

```

Change hda1 to the harddrive, this will allow read and write access..

To unmount, simply reboot or type in:
```

sudo umount /media/windows/

```

Goodluck!

---

### Post by updownleftright on 2007-01-22
Is there any way this can be automated so that when I boot to ubuntu my desktop contains icons for my old C D E and F windows drives?

---

### Post by Josh1 on 2007-01-22
> **updownleftright said:**
> Is there any way this can be automated so that when I boot to ubuntu my desktop contains icons for my old C D E and F windows drives?

Read this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---


---
title: "Mounting an encrypted external HD to an encrypted computer"
date: 2024-07-19
forum: General Help
---

### Post by Old Jimma on 2024-07-19
Hello Ubuntuers and Ubuntuites,

I did a reinstall of my computer to make it encrypted. 

I've got an encrypted external drive that I'd like to mount at startup, and use as a "backup" for my computer.

Is there anything more to mounting the external drive than:
[LIST]
[*]creating a mount point on the computer (eg, sudo mkdir /mnt/FOLDERNAME),
[*]assigning the mount point and everything within it as being owned by the owner of the /home directory, (eg sudo chown -R owner:owner /mnt/FOLDERNAME)
[*]making sure it has proper rights, like 775, (eg, chmod 775 -R /mnt/FOLDERNAME
[*]putting an entry in /etc/fstab that identifies the UUID and mount point ( eg, like this: > UUID=uuidnumber /mnt/FOLDERNAME auto nosuid,nodev,nofail,x-gvfs-name=FOLDERNAME 0 0?
[*]
[/LIST]

Thank you,
Old

---

### Post by currentshaft on 2024-07-21
> **Old Jimma said:**
> Hello Ubuntuers and Ubuntuites,

I did a reinstall of my computer to make it encrypted. 

I've got an encrypted external drive that I'd like to mount at startup, and use as a "backup" for my computer.

Is there anything more to mounting the external drive than:
[LIST]
[*]creating a mount point on the computer (eg, sudo mkdir /mnt/FOLDERNAME),
[*]assigning the mount point and everything within it as being owned by the owner of the /home directory, (eg sudo chown -R owner:owner /mnt/FOLDERNAME)
[*]making sure it has proper rights, like 775, (eg, chmod 775 -R /mnt/FOLDERNAME
[*]putting an entry in /etc/fstab that identifies the UUID and mount point ( eg, like this: ?
[*]
[/LIST]

Thank you,
Old

You need to actually decrypt it first, right?

---


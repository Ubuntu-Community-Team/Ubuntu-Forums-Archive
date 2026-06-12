---
title: "Feisty doesnt let me write to usb"
date: 2007-04-21
forum: General Help
---

### Post by lando786 on 2007-04-21
6.10 worked fine but i made a clean install upgrading to feisty and i dont have permission to write to USB media im not sure why i cant seem to find where to add myself in the users and groups section to allow me to write to usb, any help would be greatly appreciated
:guitar:

---

### Post by K.Mandla on 2007-04-21
Is this a flash drive or an external drive? If you mount it with sudo, you won't have permission unless you use sudo to write to it.

Also make sure the ownership and permissions on the drive are set for you.

Edit: That was a totally rambling and random answer. Sorry. I shouldn't try to answer questions while participating in mindless chit-chat with my co-workers. :roll:

---

### Post by lando786 on 2007-04-22
i cant change permissions on folders only set for root :( im guessing there might be a way to add me to the group that can control usbs i just dont know what group that is

---

### Post by K.Mandla on 2007-04-22
You might try adding the device to your fstab, something like this.

```
/dev/sdc1 /media/usbdisk vfat users,auto 0 0
```

Remount your partitions with *sudo mount -a* and then mount your USB stick with 

```
mount /dev/sdc1
```

That will let you mount the USB stick at sdc1 to a folder called usbdisk without using sudo. Change the assignment and destination folder as you need to.

---

### Post by lando786 on 2007-04-23
problem solved i figured out i didnt have write support for ntfs drives :-/

---


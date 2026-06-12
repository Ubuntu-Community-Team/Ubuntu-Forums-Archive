---
title: "Mounting a *.iso file without having to use sudo rights?"
date: 2007-06-12
forum: General Help
---

### Post by TuxCrafter on 2007-06-12
Hello friends,

I got a question, I want to mount an *.iso image like a cdrom or a movie without having to use sudo rights like with sudo mount -o loop ,,,, and i don't want to add mount to the sudoers list. I looked at pmount but cant seems to get that working with a *,iso file.

I currently use this work around but i am looking for something better

hostname=$(cat /etc/hostname)
user=$(whoami)
sudo bash -c "echo $user $hostname = NOPASSWD: /bin/umount, /bin/mount >> /etc/sudoers"
^^^
executed as normal user with sudo rights

The iso file is owned by the same user and will be mounted in the same directory so all the directory and the iso file have the same owner.

So does any one have a idea?

---

### Post by taurus on 2007-06-12
If it's a movie file, you can play it directory with MPlayer so no need to mount it.

```
gmplayer **filename.iso**
```

---

### Post by TuxCrafter on 2007-06-12
yes I am aware of this, but i want to be able to see the file so sort of mount, also I use xubuntu and totem-xine and it does not support playing iso directly.

changed first post a bit

---


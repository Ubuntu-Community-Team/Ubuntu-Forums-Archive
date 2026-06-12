---
title: "What's the point of using filesystem UUIDs?"
date: 2007-04-13
forum: General Help
---

### Post by Nobber on 2007-04-13
Since Edgy, Ubuntu has been using filesystem UUIDs to identify the root filesystem during boot (i.e. root=UUID=12345-whatever as a kernel boot parameter), and to identify filesystems listed in /etc/fstab - instead of the traditional devices names such as /dev/hda3 or /dev/sdb2.

Does anyone know why? I suppose there must be some advantages - like, being able to move hard disks around in a PC without worrying about device name changes, but how often do you do that? - but what prompted this post was that I was recently hit by one of the disadvantages.

I've got an oldish laptop that I use for experimenting with various distros. It has five on it at the moment. When I installed Feisty on it, I set it up so that it would automount the root partitions of the other distros under /media/fedora, media/suse and so on.

Everything was fine for a few days. Then I installed Edgy where openSUSE had previously been (/dev/hda5), and Feisty mysteriously (or so it seemed at the time) stopped booting properly. It would drop into a maintenance shell while trying to fsck the Edgy partition.

Why? Because it was trying to fsck by UUID, but installing Edgy where openSUSE used to be meant the UUID had changed since Feisty's /etc/fstab had been created, causing fsck to choke. But this wouldn't have happened if /etc/fstab had referred to /dev/hda5 instead of the UUID!

I can laugh about it now - although still somewhat hollowly - but it did lead me to wonder whether UUIDs are more trouble than they're worth.

Any thoughts?

(Incidentally, one of the amusing messages that came up after fsck's meltdown was something like "apt-get is not available; please install it using 'sudo apt-get install apt". Ho!)

---

### Post by az on 2007-04-13
> **Nobber said:**
> Feisty mysteriously (or so it seemed at the time) stopped booting properly. It would drop into a maintenance shell while trying to fsck the Edgy partition.

Why? Because it was trying to fsck by UUID, but installing Edgy where openSUSE used to be meant the UUID had changed since Feisty's /etc/fstab had been created, causing fsck to choke. But this wouldn't have happened if /etc/fstab had referred to /dev/hda5 instead of the UUID!

You found a bug.

---

### Post by m.musashi on 2007-04-13
I've had this problem too. If you change partitions anywhere then Ubuntu fails to boot (you get the maintenance shell). I have to go into fstab and fix the offending partition. So I'm not sure UUID is all that useful even for moving partitions around.

So yeah, what is the benefit of doing it this way? Is there a way to "rebuild" fstab when you make changes? Editing fstab isn't much fun.

---


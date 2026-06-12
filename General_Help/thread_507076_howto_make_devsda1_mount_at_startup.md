---
title: "howto make dev/sda1 mount at startup?"
date: 2007-07-22
forum: General Help
---

### Post by Fredrik_b on 2007-07-22
My main storage partition Dev/sda3 wont mount when Ubuntu starts. I can mount it manually via GUI, but it is an hassle to do it every time the computer starts. How do i make it mount automatically?

I have searched allot but did not found an useful answer.

---

### Post by jpkotta on 2007-07-22
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by meatpan on 2007-07-22
One solution is to edit the /etc/fstab file.  Please be aware that this is a relatively advanced operation because it requires knowledge of filesystem types, permissions, and some other lower-level details.

Hopefully someone will post the name of a helper program that can do this in a more user-friendly manner.

If not, here is some info about fstab:

/etc/fstab is an abbreviation of file-system table, and contains a list of most devices that could or should be mounted as file systems.  

To learn the dirty details, take a look at the man page, which is 'man 5 fstab'.  The '5' argument specifies the '5th' chapter of the manual, which is dedicated to config files (as opposed to chapter 1 for programs or 2/3 for programming libraries).

Hopefully there are several entries in the fstab file that are close to what you want, so you can start your editing with a decent copy of a comparable fstab entry.

EDIT: Check link in above post for a much better technique

---

### Post by Fredrik_b on 2007-07-29
Have not  looked in at this problem for a while.

It seems that the problem is that that partition is restricted, it mounts perfectly if I log in as root. I am the owner of the partition but that cant bee seen unless i manually mount it ant type in the ROOT password.

---

### Post by reaganf2 on 2008-05-19
I've got the same problem...
I'm new to ubuntu and not at all comfortable editing the fstab file...
I would however love to have my windows partitions sda1 and sda5 mount at startup without having to do it manually each time after booting...
I'm running hardy heron...

---


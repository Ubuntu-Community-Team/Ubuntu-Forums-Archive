---
title: "Some problems with the live cd"
date: 2005-10-30
forum: General Help
---

### Post by tmmuk on 2005-10-30
Hi, my computer got messed up during an upgrade from hoary (see the thread I made in the desktop section subforum) and I am trying to use the live-cd version of breezy to backup my files onto another computer on the network before I format my hdd and start from scratch.

A few problems I have had with the live-cd:
- It does not show the contents of my hdd, and all my original files from my hoary version (that was installed on my hdd). It shows a (virtual -i think) hdd that has none of my stuff on it. How can I get it to show me my actual hdd? (i need to be able to see my real home dir and other dirs for backup purposes)

- I locked the computer, but do not know the password to unlock it (it never asked for me to set one, so I dont know what it is). Is there a default password that will work?

any help would be great thanks

---

### Post by shinygerbil on 2005-10-30
Off the top of my head (i.e. may not be perfectly accurate):

Create a directory to mount the HDD onto (for example /mnt)

In the console, type:

```
sudo mount -t ext2 /dev/hdaX /mnt
```

where X is the number coresponding to your Hoary hdd, and /mnt is the directory you created in the first step.

Note: If this doesn't work, try replacing ext2 with ext3. I'm also not sure whether the sudo is necessary on the LiveCD.

Hope this helps

Steve

---

### Post by tmmuk on 2005-10-30
[QUOTE=shinygerbil]
In the console, type:

```
sudo mount -t ext2 /dev/hdaX /mnt
```
[/QUOTE]

cheers, it worked :)

now all I kneed to know is how to completely wipe my hdd? would it work just by putting the linux install cd in and chosing to overwrite the partitions? or do i need to delete the current copy of breezy (the broken copy) first?

---

### Post by beefsprocket on 2005-10-30
If you've backed everything up, just use the standard install disc and choose use whole disc (hda I'd imagine) when you come to the partitioning section.

You can also use fdisk from the live cd to create a new partion scheme, but since you'll be reinstalling anyways from the sound of things, just use the install disc to do the partition work for you.

---


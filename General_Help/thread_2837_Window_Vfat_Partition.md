---
title: "Window Vfat Partition"
date: 2004-11-01
forum: General Help
---

### Post by riveraca on 2004-11-01
I just installed UBUNTU ... if I try accesing a WINDOWS VFAT partition using the "file explorer" I can see the name of the files at the first level but i cannot do anything, i.e., open directories, view files, copy files, etc.... from the "file explorer"...

I have mounted the WINDOWS PARTITION using the following command :

     mount -t vfat /dev/hda2 /mnt/winXP

I can copy, move using the "TERMINAL PROMPT"

Does anyone know what do do to:

1. What needs to be done so I can have access to the WINDOWS partiton using the "file explorer" in GNOME?

2. How can the WINDOWS PARTION be loaded automatically everytime the PC is restarted.

Thanks ... CARLOS

---

### Post by cacofonix on 2004-11-01
Welcome to ubuntu riveraca to mount the windows partition on boot add this to fstab
```

<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda2         /media/winXP      vfat      defaults,users,rw  0              0

```

You will need to reboot to load the changes, when you log in again if you go to media there should be a icon for windows and you should be able to look around to your hearts content. *note if you only want to get files from the partition and not copy files to it change rw (read write) to ro (read only)*

cacofonix

---

### Post by kamstrup on 2004-11-01
You need to edit the file /etc/fstab. You can do this with 'sudo gedit /etc/fstab'. Here you add a line like this to the bottom:

/dev/hda2   /mnt/winXP   vfat   default   0   0

Make sure that fstab still ends with a blank line (I don't know if this is still important, but I think it once was :wink: ).

You can also mount ntfs partitions this way. Just substitute 'vfat' with 'ntfs'. Good luck.

kamstrup

---

### Post by luiska on 2004-11-01
Is NTFS supported "out of the box" on Ubuntu? The few times I tried it on Fedora and Redhat you needed to insert a module. And there was always big warnings about it.

Luiska

---

### Post by ynef on 2004-11-01
[QUOTE=luiska]Is NTFS supported "out of the box" on Ubuntu? The few times I tried it on Fedora and Redhat you needed to insert a module. And there was always big warnings about it.

Luiska[/QUOTE]
 NTFS read support is supported out of the box (yes, as a kernel module, but it makes no practical difference), since it's a standard feature included in the linux kernel. Writing to NTFS volumes is currently (fall 2004) considered very experimental, but that will most likely change in the future.

If you require full write support, there's the Captive project that uses Wine and the dll for Windows' handling of NTFS, which (as far as I've heard from buddies who have tried it) seems to work correctly. However, I'd stay away from it for production use.

The warnings are simply warnings -- unless they tell you something that needs to be adressed, you don't need to worry about it.

---

### Post by ken on 2004-11-01
um... the example lines provided look alright but when I tried those lines, only the root had access to the vfat partion.

The line I have in my fstab is:

/dev/hda6	/mnt/data	vfat	rw,auto,uid=1000,gid=1000,umask=0000 0	0

/dev/hda6 : my partition
/mnt/data : the mountpoint
vfat : filesystem type
rw : read/write mode
auto : automatically mount (at startup or with the mount -a command)
uid=1000 : my userid
gid=1000 : my groupid
umask=0000 : affects the permissions (all files created with 777)

I never really did figure out what to do with the last 2 0's on the line.  It has something to do with the auto mounting but I keep on forgetting what.

The uid and gid options on the line mounts the directory as with the uid and gid specified.  By using my uid and gid, I have full access without having to su or sudo anything.

Hope this helps.  And if I'm wrong about any of this, can someone correct me?

Ken.

---


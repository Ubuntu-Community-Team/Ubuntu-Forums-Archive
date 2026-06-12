---
title: "Two different Snap installed applications refuse to recognize an NTFS parition"
date: 2023-02-09
forum: General Help
---

### Post by xanizen on 2023-02-09
The NTFS partition was created with Windows 7 (now un-installed in favor of Ubuntu).

The partition was 'mounted' or assigned a directory of /sdd1 during system installation of Ubuntu.

This is the permission of the NTFS partition:
```
$ ls -ld /sdd1
drwxrwx--- 1 vhen vhen 4096 Feb  9 21:45 /sdd1

```

This is what is shown in the fstab file.
```
# /sdd1 was on /dev/sdd1 during installation
UUID=A85A808D5A8059C8 /sdd1           ntfs    defaults,uid=1000,dmask=007,fmask=007,umask=007,gid=1000 0       0
```

I manually specified the dmask/fmask because supposedly NTFS ownership can't be changed from 'root' to user.

The applications in question can acknowledge files from removable media, in this case a veracrypt partition.
The command, sudo snap connect <app name>:removable-media, worked as intended.

The partition directory isn't listed when I open the 'file picker' from the Snap apps. Also dragging the file from explorer onto the Snap apps, results in nothing happening.

---

### Post by deadflowr on 2023-02-09
Removable media only includes directories inside ether the /media or /mnt locations.

---

### Post by MAFoElffen on 2023-02-10
I'm sorry for your loss... 

Do you think people might respond appropriately if you named which specific snap applications you cannot use? Then they might recognize how to use those applications, and possible limitations or work-arounds for... Me, for one, am confused by what you are asking for or about. And I am usually good at figuring out riddles.

Please do not make them "guess" what you are trying to use. People have difficulty reading minds.

Please be clear and concise.

---

### Post by Impavidus on 2023-02-10
For your actual question, I think deadflowr nailed it. But there's something different I'd like to draw your attention too:
> **xanizen said:**
> The NTFS partition was created with Windows 7 (now un-installed in favor of Ubuntu).
So you've got an NTFS partition, but no longer a Windows system. The Linux tools on your system cannot defrag an NTFS filesystem or fix it if damaged, so it's best to avoid NTFS if you're running Linux only. No hurry if you've got backups, but keep in mind that if your filesystem gets damaged, it may be hard to recover files from it.

---

### Post by TheFu on 2023-02-10
> **deadflowr said:**
> Removable media only includes directories inside ether the /media or /mnt locations.

A little clarification to this ... 

snap packages support accessing files from 1 place by default.  /home/{username}
If a snap packaging team decides, they might allow "removable media" locations to be manually added.  Removable media locations add storage locations mount under /mnt/ or /media/.  

BTW, I think the fmask, dmask, umask all require 4 octal values in the mount command. Just add a leading '0'.  And having the umask along with the fmask/dmask is odd. I don't know that that will do.

So ... your fstab should probably look like this:
```
UUID=A85A808D5A8059C8 /media/d1           ntfs    defaults,nodev,windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,dmask=0007,fmask=0007     0       0
```
I moved, added and removed a few things to improve stuff.  That's a single line.

Another option is to not use UUIDs, but LABELs.  Humans can understand a LABEL and we are terrible at understanding UUIDs (random stuff).  If you add a LABEL to the file system (use gparted), then you can mount it using "LABEL=someName" anywhere the "UUID=" is used.  Much more useful for humans.  Just don't reuse the same label for storage connected to the same system concurrently.

If the storage is USB, and if you go to this effort, maybe using 'autofs' rather than the fstab would make sense?  Only you can answer that question.

---

### Post by xanizen on 2023-02-10
> **TheFu said:**
> A little clarification to this ... 
So ... your fstab should probably look like this:
```
UUID=A85A808D5A8059C8 /media/d1           ntfs    defaults,nodev,windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,dmask=0007,fmask=0007     0       0
```
I moved, added and removed a few things to improve stuff.  That's a single line.


This solved the problem of the 2 applications, thank you for the solution.

---

### Post by DuckHook on 2023-02-10
Though your problem is superficially "solved", you really should pay attention to Impavidus's point: If your whole setup is now Linux, then NTFS is bad news. It bodes nothing but much future wailing and gnashing of teeth.

---


---
title: "exaile or listen library"
date: 2007-10-25
forum: General Help
---

### Post by dayvy on 2007-10-25
I want to be able to play music from a library that is sitting on a server. The directory is mounted via nautilus using either samba or ssh (Connect to Server...). The directory shows up in nautilus under the left pane places menu and I can access all the files there. When I use Rhythmbox I can see this directory and use it as a library. However, when I use Exaile or Listen I cannot see the directory when I try to import a directory or library. Any ideas on how to solve this? I was in the past mounting the directory via fstab and samba but that has been problematic because I use wireless and fstab seems to load before my wireless nic is connected.

Thanks,
d.

---

### Post by jfrorie on 2007-10-26
> **dayvy said:**
> I want to be able to play music from a library that is sitting on a server. The directory is mounted via nautilus using either samba or ssh (Connect to Server...). The directory shows up in nautilus under the left pane places menu and I can access all the files there. When I use Rhythmbox I can see this directory and use it as a library. However, when I use Exaile or Listen I cannot see the directory when I try to import a directory or library. Any ideas on how to solve this? I was in the past mounting the directory via fstab and samba but that has been problematic because I use wireless and fstab seems to load before my wireless nic is connected.

Thanks,
d.

I think only nautilus and gnome comliant apps can see nautilus mounts.  It's a gnome thing.  To get it at a lower level, you will need to "mount" or fstab it.

Jim

---

### Post by dayvy on 2007-10-26
I think you may be right. Looks like i'm going to go the autofs route. 

Thanks,
d.

---


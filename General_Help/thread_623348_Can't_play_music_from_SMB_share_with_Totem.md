---
title: "Can't play music from SMB share with Totem"
date: 2007-11-25
forum: General Help
---

### Post by phoenixnr on 2007-11-25
Can't play music from SMB share with Totem or XMMS. Works with MPlayer. Can play any file with any player locally. Anyone?

---

### Post by apetresc on 2007-11-25
How are you accessing the Samba share? Are you actually mounting it with something like smbfs, or just using Gnome's "connect to server" feature, or what? Could it be a duplicate of this old bug here: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/70329](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/70329) ?

---

### Post by phoenixnr on 2007-11-25
Dont think so I try the command they suggest in that thread and it comes up with all the shares...

---

### Post by phoenixnr on 2007-12-01
Anyone?

---

### Post by komputes on 2008-02-18
I'm using VLC, and it does not want to play music off any share (smb://)

---

### Post by AlanR8 on 2008-02-18
My experience is you have to mount the external drive to ensure everything just works. That said, VLC plays from this lap top when accessing via samba shares to a remote computer.

---


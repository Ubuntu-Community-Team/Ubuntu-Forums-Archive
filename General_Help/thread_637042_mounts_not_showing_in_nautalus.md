---
title: "mounts not showing in nautalus"
date: 2007-12-10
forum: General Help
---

### Post by drzoo2 on 2007-12-10
I'd like an entry I added to fstab to show in the computer:/// location on my gusty box like the local hard drives and DVDROM drives. The mount refers to a file server and works fine but I'd like it to show up in Nautilus > places as if I plugged in a USB hardrive or thumbdrive.

Any thoughts?

The connect to server option works but this isn't a real mount point.
z

---

### Post by stump138 on 2007-12-10
try doing a cd /network/share/name from a prompt.

NFS shares won't show in nautilus it seems at the moment unless you specifically call them.  I create a shortcut to nfs mounts on my desktop so I can look at them in nautilus as they won't show up.

---

### Post by drzoo2 on 2007-12-10
> **stump138 said:**
> try doing a cd /network/share/name from a prompt.

NFS shares won't show in nautilus it seems at the moment unless you specifically call them.  I create a shortcut to nfs mounts on my desktop so I can look at them in nautilus as they won't show up.

I should have specified I'm using cifs since I have one windoze box and XBMC running. I've created a shortcut to my mount point. Just be nice if Nautilus picked it up as a place without using connect to server. I'd rather it use the actual mount vs a link to the remote box.

z

---


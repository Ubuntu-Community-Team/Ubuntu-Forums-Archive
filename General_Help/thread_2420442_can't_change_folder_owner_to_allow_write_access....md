---
title: "can't change folder owner to allow write access..."
date: 2019-06-05
forum: General Help
---

### Post by royalba94 on 2019-06-05
Hey all!

So I've been battling with trying to setup my SMB shares for several hours now and in all my googling can't seem to figure out the solution.

The problem as I've identified it is that my user doesn't actually have write permissions to the folders where I mounted the shares via fstab. I am able to read/write files is I browse to the other locations > servername > sharename but not if they're mounted via fstab.

I've tried using chown and chmod on the files along with sudo nautilus to change the owner/permissions but get no output or it changes back instantly - also tried changing the force user value in the smb.conf but no luck.

Here's what I've got for fstab:

[IMG]https://i.imgur.com/6oyHQih.png[/IMG]

and here's what I've got for smb.conf on the server (for one of the shares, they're basically the same):

[IMG]https://i.imgur.com/6QssJ7N.png[/IMG]

Server: Proxmox running Samba - shares are ZFS pools
Client: Ubuntu using fstab to mount shares so that I can point Plex and Nextcloud to those shares (they're running in SNAP)

Hopefully I provided enough info but if not LMK and I'll be happy to get you more if it helps you help me - thanks!

---


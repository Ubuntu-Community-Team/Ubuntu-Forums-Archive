---
title: "Streaming media through samba"
date: 2006-11-13
forum: General Help
---

### Post by ffunk on 2006-11-13
With the recent update of edgy, I can't seem to stream any media which is located on a win xp machine.  I'm aware of the current bug with totem [https://launchpad.net/distros/ubuntu/+source/totem/+bug/61147]("https://launchpad.net/distros/ubuntu/+source/totem/+bug/61147"),  but it seems like every media player has the same problem.  I read that it has something to do with gnome-vfs.  If so, would rolling back to the Dapper version solve this problem?

Any help would be greatly appreciated.

---

### Post by harty83 on 2006-11-14
What exactly do you mean stream? I'm using amarok under edgy to access my mp3s on a samba share that I have on another linux box.  Everything works fine.

Occasionally, something happens to my samba share connection and all my music players will lock up trying to access it.  All I do though is unmount and remount it.

Can you access the samba share?  Browse, edit, etc?

If you are simply accessing the share via smb://etc directly through the player, then you may try to mount the share and then direct your player to the mounted folder.

---


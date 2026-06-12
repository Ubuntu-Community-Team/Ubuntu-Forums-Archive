---
title: "Problem with BitTorrent"
date: 2007-12-05
forum: General Help
---

### Post by davibbarbosa on 2007-12-05
Hi folks,
BitTorrent was working properly, but it stopped cause there was no space left to download the file. Then I ctrl+X'ed the file I was downloading and placed it somewhere else. Then I double clicked the .torrent again, to resume the operation, but it won't work anymore. I tried downloading another .torrent, but all the .torrents I find link to the same place.
Anyone, any idea how to fix this?

---

### Post by lswest on 2007-12-05
change the default destination in bittorrent under preferences (probably under edit--> preferences, not sure though, as i dont use bittorrent much).

---

### Post by davibbarbosa on 2007-12-05
Well, BitTorrent is the default torrent program in ubuntu, so I don't even need to open the application, just double click the .torrents... Where can I change this preference?

---

### Post by lswest on 2007-12-05
i'm pretty sure when you start downloading a torrent a new window shows up, i also believe it has a menubar, wherein you can change the default directory.

---

### Post by davibbarbosa on 2007-12-05
The problem is that I cannot open it anymore... when I double click the .torrent, the cursor changes to the "waiting mode", then back normal and nothing happens :(

---

### Post by lswest on 2007-12-06
try reinstalling the bittorrent package with "sudo apt-get install --reinstall gnome-btdownload" i believe that is the name for the package.  that should solve your problem of not being able to open it.

---

### Post by davibbarbosa on 2007-12-06
Thanks!
I'll try that as soon as I get home.

---

### Post by silviutp on 2007-12-06
Hi,

I have a problem with Bittorrent.

I've just installed the package (bittorrent && bittorrent-gui ) with the packet manager but I cannot find the client.

Did someone encounter this issue ?

Thanks.

---

### Post by davibbarbosa on 2007-12-07
Reinstaling "btdownload" didn't work :|

---

### Post by davibbarbosa on 2007-12-07
Well, in a way... problem solved. I couldn't fix BitTorrent problem, so I downloaded another client, **Deluge**. It's working fine and is very intuitive.

silviutp: Isn't it in Applications >> Internet ??

---

### Post by Tenken on 2007-12-07
By default the bittorrent client isn't displayed in the gnome menu, but it will automatically start when you try to save/open a .torrent file. If you want to have the client in the menu just because right click the menu goto Edit Menus->Applications->Internet and click the check box next to bittorrent.

---


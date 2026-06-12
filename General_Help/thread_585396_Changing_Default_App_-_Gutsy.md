---
title: "Changing Default App - Gutsy"
date: 2007-10-21
forum: General Help
---

### Post by mpierce on 2007-10-21
Using Kubuntu and have posted in their forum but not as good as this forum. 
Just upgraded from Feisty. All appears to be working after a few errors.

I'm trying to change a default application as I want to use Deluge as the default bittorrent client in lieu of KTorrent. This is what should work (what I've done) but it doesn't work:

1) Open kcontrol
2) Select KDE Components / File Associations
3) Enter torrent in find pattern box
4) Application x-bittorrent appears
5) I remove Ktorrent and add Deluge
6) Click Apply

Oops not working, I then remove kTorrent from system and reboot.

When I download a torrent, it tells me to change preferences. Duh...
Am I missing something here as I check file associations again and only Deluge is there.

---

### Post by Maestro23 on 2007-10-21
Are you clicking on the torrent in Firefox?  If so, tell FF that you want to use Deluge as the default torrent client.  Edit>> Prefs>> Content>> File Types

I have Ktorrent set up this way and I'm running Gnome.

---

### Post by mpierce on 2007-10-21
> **Maestro23 said:**
> Are you clicking on the torrent in Firefox?  If so, tell FF that you want to use Deluge as the default torrent client.  Edit>> Prefs>> Content>> File Types

I have Ktorrent set up this way and I'm running Gnome.

Thanks for the reply. I'm using SwiftFox but that shouldn't matter as it's the same. 
It was there showing that it should open with the default app, deluge but it wasn't working. I deleted it and told it to open using a specific app (2nd radio button), /usr/bin/deluge. It is now working.

Try deluge! It has far superior to KTorrent with control over downloading individual files and has plugins that give it the power of Azureus (my least favoruite as it can be a dog, ram hog, prima donna as to which java, etc) or my favourite, uTorrent.

---

### Post by impalerau on 2007-11-01
> **Maestro23 said:**
> Are you clicking on the torrent in Firefox?  If so, tell FF that you want to use Deluge as the default torrent client.  Edit>> Prefs>> Content>> File Types

I have Ktorrent set up this way and I'm running Gnome.

After installing and trying various clients, I've settled on KTorrent.   I've set KTorrent as the default association in ubunto so when I double-click in PCMan the file opens in KTorrent.  

But when I click on a torrent in Firefox I get a popup and the only "open with" option available is "Bittornado Client (default)".  The only file types listed in the Firefox "File Types" dialogue are multimedia types and there doesn't seem to be any option to add types.  

Where am I going wrong?

Vlad

---

### Post by impalerau on 2007-11-01
Sorted.  Looks like PCMan isn't well integrated into the desktop.  Set file association in Nautilus (Right-click >> Properties >> Open with) and it's all fine now.

---


---
title: "Restore ubuntu basic configurations"
date: 2019-12-23
forum: General Help
---

### Post by abelncm on 2019-12-23
Hello

I wanted to install Deepin Boot Maker so i found a solution online to add deepin ppa, but as soon as i updated/upgraded through apt it changed some configurations from ubuntu.

On gnome's about it shows deepin.
On Software and Updates it changed some texts to debian's.

[IMG]https://drive.google.com/open?id=1tV3PTlRB_Fjtz3b9AEasgkrEv1h_VJxI[/IMG]
[https://drive.google.com/open?id=1GAHgKUoZnLxq7QXo0adRN_EbtCSGcZx-](https://drive.google.com/open?id=1GAHgKUoZnLxq7QXo0adRN_EbtCSGcZx-)
[https://drive.google.com/open?id=1tV3PTlRB_Fjtz3b9AEasgkrEv1h_VJxI](https://drive.google.com/open?id=1tV3PTlRB_Fjtz3b9AEasgkrEv1h_VJxI)

I know this isn't a big deal, but it may as well have changed something else. My question is, is there a way I can restore ubuntu's configurations without losing anything or breaking my OS?
I already did ubuntu's desktop enviroment reinstall.

I have ubuntu 19.10

---

### Post by TheFu on 2019-12-23
Did you make a backup BEFORE adding the PPA?  That's the only way I know.

If you want something like "system restore points", that doesn't exist on any Unix, but you can trivially accomplish the same thing.

Backup all settings in /etc/ and the list of manually installed packages using **apt-mark showmanual**.  Save that command output to a file.  These 2 things are relatively tiny. But if you've gone that far, for most desktop-only-users, just backing up /home/ will get everything they need to have a system backup.

With those 3 things, you can probably recreate a system that feels exactly the same as before the backup in about 45 minutes, perhaps just 30 minutes.

Obviously, if you store other files or install programs to other directories, you'll want to back those up too.  Perhaps you downloading tgz files, compile and install those programs to /usr/local/  ... then you'd want that area in your backup set.

I don't know what to do about snap packages. Perhaps getting a list of those from **snap list** would be sufficient?  I don't use snaps at all.

With a good, versioned, backup tool, doing these backups daily or weekly should take just a few minutes.  I do daily backups for all my systems.  Each is usually just 2-4 minutes.  The first backup for each system does take a little more time, since it is effectively creating a mirror of all those files.  After that, only changed/new files get included, so it is very fast.

---


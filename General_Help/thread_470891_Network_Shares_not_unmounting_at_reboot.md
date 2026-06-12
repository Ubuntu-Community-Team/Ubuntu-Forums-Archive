---
title: "Network Shares not unmounting at reboot?"
date: 2007-06-11
forum: General Help
---

### Post by Meese on 2007-06-11
I have directories shared via Samba on a couple Ubuntu machines.  On another Ubuntu box, I add lines into my /etc/fstab to mount the shares at boot up.  I have the mount points created and from terminal when I 'mount -a'  the mount points are done properly and I can access my shares as expected.  

However, whenever I reboot the box, the shares are no longer accessible.  The directories appear as files when viewed in nautilus (there is of course a decent delay opening up the parent directories while the mount points are trying to be accessed).  My current solution is to unmount the shares, and then re-mount them via 'mount -a'.  This seems to defeat the entire purpose of adding the fstab entries.

For reference, my /etc/fstab entries for the mounts are...
> //192.168.1.200/Storage /home/Pacman/Turbodog smbfs auto,credentials=/home/Pacman/.smbcredentials,uid=1000,gid=1000 0 0
//192.168.1.220/media  /home/Pacman/Purplehaze smbfs auto,credentials=/home/Pacman/.smbcredentials,uid=1000,gid=1000 0  0


Ive done a bit of digging around through forums and havent quite stumbled on anything exactly as Ive noted.  Are the mount points simply not beeing unmounted at reboot which inturn causes the problem when the box comes back up?  I saw a couple threads where people said they had similar problems with SMB shares when their machines came into/out of hibernation or suspend modes.  Would this be anythign similar?  Is /etc/fstab beeing run prior to the network coming up fully which keeps the network shares from beeing mounted?  Or am I just missing some glaringly obvious problem?

Thanks for any help.

---

### Post by DugieHowsa on 2007-06-27
You should try using cifs.  This post states that smbfs is unstable and no longer under active development:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

The following is also a very good post on how to configure cifs and gives a few examples on how to automatically mount cifs shares at boot.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---


---
title: "md5sum not adding up"
date: 2008-05-05
forum: General Help
---

### Post by Foomandoonian on 2008-05-05
I have downloaded several Ubuntu variations recently, and have not been able to produce a CD that works. I know enough to check the md5sum, and these numbers have never matched up.

I have tried:

**ubuntu 8.04** (via torrent AND http download)
**kubuntu 8.04** - KDE4 version (via torrent)
**ubuntustudio 8.04** (via torrent)

Each from a different mirror source (including the Canonical UK one)

None of these numbers matched. (Curiously, I have also tried a Debian KDE release which failed, but I burned the iso for that a while ago and forget the details.)

Now, I know my process is not off because I have just today succesfully downloaded, checked and run **Simply MEPIS 7.0**, **PCLinuxOS 2007**, and yesterday **Puppy Linux**, all with no problems.

ANY help would be appreciated, as I'm eager to try the latest Ubuntu, especially Kubuntu.

Thx.

---

### Post by daengbo on 2008-05-05
If you're having that much trouble getting the full iso (there are many downloaders right now), you might consider a network install.
 mini.iso 22-Apr-2008 10:04  9.5M 
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/mini.iso)

This will download the current packages one-by-one. You should have no problem if you use wired networking with DHCP. There's no live CD/desktop for this, but the text installer is really straightforward.

---

### Post by Foomandoonian on 2008-05-05
Thanks for the reply, daengbo. I think I understand your suggestion, but it seems a little out of my comfort zone, to be honest.

I have trouble believing that all 4 (or more) downloads have failed. Do you think it's really that straightforward? I thought that bit torrent downloads was a more reliable method for downloading complete files!

Does anyone else have any further insights into this?

---

### Post by daengbo on 2008-05-05
If the MD5SUMs aren't matching, then you aren't getting good copies. That's the bottom line. This could be for many reasons: poisoning in torrents, too many downloaders, bad networking hardware, etc. Because of the heavy load on the Ubuntu servers right now, I suggest that you either wait for a couple of weeks or do a network install. The network install isn't difficult.

---


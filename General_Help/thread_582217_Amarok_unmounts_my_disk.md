---
title: "Amarok unmounts my disk"
date: 2007-10-19
forum: General Help
---

### Post by Zalbor on 2007-10-19
I keep my music files in an NTFS partition on an external hard drive, connected by a USB cable.
I don't (manually) use pmount nor are there entries for this disk's partitions (3 in total) in fstab.
I use Amarok to play music, and every time I close it (Amarok) a few seconds later all 3 partitions get unmounted. This began happening after I installed Gutsy.
Is it an option in Amarok that I forgot to change? I can't find something relevant.
I'm using Gnome.

---

### Post by MusicMastaMike on 2007-10-19
I'm getting the same problem with a FAT32 external hard drive.  Same deal, just started happening after I upgraded.  This is really quite a problem for me... Help would be greatly appreciated from both of us!

---

### Post by MusicMastaMike on 2007-10-20
I got this figured out!  What I had to do was manually add my USB drive to fstab with the following line:

> /dev/sdb1	/media/FAT32	vfat	user,auto,fmask=0111,dmask=0000	0	0

This took care of all the amarok unmounting woes.  Good luck!

---

### Post by Zalbor on 2007-10-20
I knew that... But the problem is that this way if I want to unmount and remove the disk, I have to unmount as root. I'd like to still be able to do it with the applet on my panel.

---

### Post by tisk on 2007-10-20
I have this problem with amarok with a mounted internal secondary drive (ext3). But also I can no longer get playback in amarok. This all happened since I updated to gutsy.

---

### Post by neverett on 2007-10-22
Has someone submitted a bug about this issue yet?  If so, please post the bug number back here please!

---

### Post by shad0w_walker on 2007-10-22
You might want to try this:

Add the drive as if it was a MP3 player (In the Devices tab) and then goto Configure and set the pre-disconnect command to something like /bin/false which should make it run that instead of its usual disconnection script and seeing as false does nothing it should leave the mount alone.

P.S. You should still file a bug report about this even if it works.

---

### Post by tisk on 2007-10-22
By the way I found a full reinstall of amarok fixed any bugs I had since installing gutsy.

---

### Post by Zalbor on 2007-10-23
Personally, I went back to using Rhythmbox. I had stopped because of some sound issues, but in 7.10 they're not there. So I'm off Amarok...

---

### Post by cdyson37 on 2007-10-23
Settings->Configure->Media Devices and then remove all devices (at least those relating to your external hdd) appears to work.

---

### Post by yostral on 2007-10-23
I have this bug too, and not only with amarok, but other KDE apps (like k9copy) running in Gnome.

I filled a bug  [in launchpad]("https://bugs.launchpad.net/ubuntu/+bug/156213"). You can confirm it :).

---

### Post by craigyjack on 2008-02-04
I have this problem too. I store my music on an external harddrive formatted FAT32. Amarok unmounts it when I close amarok.
This is annoying, I have to remount it with the disk mounter panel applet everytime i close amarok (or boot amarok up and realize i never remounted it).
This kinda scares me as well, because i dont know what would happen if I am using a file on my external drive when amarok closes, if it would eject the harddrive in use and hurt it. I hope this bug gets fixed, its a horrible bug and I don't know why amarok would be doing this.

Also, removing my drive from the devices settings in amarok did not solve the problem as suggested. and from the launchpad bug, this looks to be a kde on gnome problem, not just amarok.

---

### Post by cdyson37 on 2008-02-10
Doesn't happen to me very often now, but if it's still an issue you could try taking your disk out of the hands of amarok and the userspace mounting system and just add an appropriate line to fstab.

---


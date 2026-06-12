---
title: "Keyboard not responding after my bad idea"
date: 2007-02-20
forum: General Help
---

### Post by jketvirtis on 2007-02-20
I'm running Kubuntu Edgy on a Compaq Presario 2500.  Yesterday, I decided to switch from the power manager that comes packaged with Kubuntu to the KDE-standard Kpowersave.  It seems to also have changed the power save daemon, but I'm not sure from what to what.  I also added a resume entry to my grub list so that I could hibernate the laptop.  When I rebooted for the first time after that, I received an error along the lines of "Kernel panic - not syncing.  VFS: unable to mount root fs on unknown block (0,0).  After a lot of hair-pulling, I was able to use the live cd to run update-initramfs -u, which seemed to fix things.

At this point, to get the X server running and see my KDM login screen.  However, when I go to type in my password, nothing happens.  I think the computer sees the keyboard, because it recognized when the caps lock was on.  It also doesn't recognize the keyboard when I used to recovery mode and "startx".  I'm kind of at the end of the line for ideas from my end, but I'd really like to avoid having to reinstall.  Any help anyone can provide would be great.

Thanks in advance.

-Jud

---

### Post by jketvirtis on 2007-02-20
One thing I forgot to add was that I also had to run "reiserfsck --rebuild-tree" on my kubuntu partition.  I'm sure something as traumatic as this could have just ruined my partition, though I am able to access it from the Live CD and windows to save some of my important files.

---


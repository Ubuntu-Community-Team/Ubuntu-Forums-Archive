---
title: "LTSP in 14.04 Screen Lock Issue"
date: 2014-10-13
forum: General Help
---

### Post by pat-rynoceris on 2014-10-13
This is now a duplicate thread. I posted in the 'Desktop Environment' Sub-Cat but upon further review, this section seemed more fitting. Not sure how to delete the other one so if a moderator would like to assist, that would be great!

Hello all!

Firstly, I'm not sure where to put this post, so I hope I got it (somewhat) right. I very recently moved a doctors office using Windows Server 2008 over to a diskless thin-client environment using LTSP on an Ubuntu 14.04 VM as a passthrough. One of the original developers of LTSP had to assist with this integration, so I know the code is right.

While the clients are booting as they should via RDesktop, the screen blanks after ~5min, causing the RDP session to lock, only allowing the logged on MS user to get back in. This causes HUGE problems since all the workstations are accessible by all employees.

I am sure this not a Server 08 issue as I have checked and rechecked the applicable GPOs and registry items.

I have checked lts.conf and X_BLANKING=0

Any help on this would be greatly appreciated as I fly out tonight.

Thanks!!!

---

### Post by pat-rynoceris on 2014-10-13
So this was an issue with the pxe image settings, and was solved by:
1: ltsp-chroot
2: set org.gnome.desktop.lockdown disable-lock-screen 'true'
3: set org.gnome.desktop.screensaver lock-enabled 'false'
No rebuild of image required for this install, simply reboot your thin client!
It is worth noting that this does not disable screen blanking, simply the lock.

---


---
title: "Troubling Log in Loop; Not like other's have described."
date: 2016-02-04
forum: General Help
---

### Post by Rushlight on 2016-02-04
Hello Ubuntu community. This morning while working on my homework on my dell 17 7737 (i7 dual core, 2.7GHz turbo, 16g Ram, GX 750m) , my update manager crashed. i ended up getting a phone call so i closed my lid, put the computer to sleep, etc. when i came back the screen was pure black. [Using ubuntu 14] 

though a bunch of backtracking i'v come to the conclusion that my nividia driver is what crashed the update, and screwed up the whole X server by not fully updating. (it made changes but did not complete. i had to purge all my graphics drivers and xconfig files)

by using the ctl, Alt, F1 access to the terminal before the login i was able to reinstall/reconfigure packages/fix the Nvidia Driver till the login screen would show, but then i got the login loop problem that other users have been having. every time i try to log in it goes black and skips to the login screen. i've tried all the fixes so far on this forum, checking the .Xauthority, reinstalling ubuntu desktop, unity, etc, etc.

i was originally able to access guest, but then after another reboot i  was locked out via the loop from that too. i tried creating another  user, both as admin and root, but their profiles didn't show up on the  login screen, therefore i couldnt use tem to get into the x server.  startx doesnt work, the x server crashes.

in my last effort i installed the Full Gnome Shell, someome said it would overwrite the problem and let me log in. now my grub screen is green and once ubuntu gets bast the gnome loading screen it flashes black constantly and doesn't respond to any keystrokes. it's basically bricked unless i access the root utility though the advances boot options.

i was originally able to access guest, but then after another reboot i was locked out via the loop from that too. i tried creating another user, both as admin and root, but their profiles didn't show up on the login screen, therefore i couldnt use tem to get into the x server. startx doesnt work, the x server crashes.

How do i fix this. 
is there a way to reset/re-install the Xserver? or set everything back to default? (like windows restore)
all my data is on my windows partition, so i have nothing to loose if i have to wipe it.

---

### Post by lisati on 2016-02-04
*Thread moved to **General Help**.*

The Resolution Centre is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse.

---


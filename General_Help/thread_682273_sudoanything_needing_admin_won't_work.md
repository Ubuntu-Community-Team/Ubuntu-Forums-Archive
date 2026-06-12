---
title: "sudo/anything needing admin won't work"
date: 2008-01-29
forum: General Help
---

### Post by myke on 2008-01-29
Does anyone have any idea what I might have done to destroy my ability to launch any program requiring a sudo or root login?   Whether via terminal or something as simple as the updater applet, I can't access anything that requires putting in a password with admin privileges.   I have my system set up where I can login as root under the GUI which should mean I can access anything but even logging in as root directly under gnome or kde does not allow me admin program access.

I can't make any changes in the system settings, make any updates, etc.   All I can do is run things as they are so I'm basically stuck with things as they are period.

What file might I have corrupted or possibly altered and messed up that could cause such problem??

PLEASE help if you know what this might be.  I dread the thought of doing yet another clean install which I've already done 3 times with Gutsy due to various problems caused by normal updates.  Now I think I caused this problem some how when trying to fix a mount problem with my portable drive but I don't know what I did that messed things up.

---

### Post by myke on 2008-01-29
PS -- It would be awfully helpful if K/Ubuntu had a repair installation or restore point utility built in to the live cd or in the settings panel.  I had to compare ... but even my xp partition has this which often saves me from the horrible wipe and start over scenarios that I'm getting sick of with K/Ubuntu.  I don't mean to rant but damn have these upgrades gotten more problematic.   I know I'm not alone as I've read lots of posts saying the same thing.  Bugs are carried from update to update.  The maintainers (hello?????) seem to worried with the regular update cycle rather than keeping things running smoothly.  Each upgrade from breezy all the way to gutsy has been much much more buggy.

---

### Post by bodhi.zazen on 2008-01-29
kde uses kdesu rather then gksu (for graphical apps)

Check your group memberships, you need to be in the admin group to use sudo

---

### Post by myke on 2008-01-29
Hey, thanks for the suggestion.  I have my id in the admin group and every other group I could think of that might help including a sudo group itself.  Didn't help.

Remember one thing though (this is why I think it's a file I messed up some where) ... I have it set where I can login under root with the GUI.   So even when I do that root itself can not launch any program requiring a password.  The password prompt never even comes up.   Synaptic, gparted, adept, the updater ... anything like that I can not access.   

I had planned on repartitioning my external passport drive which is currently formatted in NTFS with a FAT32 partition as well so that I could access it with the live cd and perhaps try moving some of the original system files to the portable drive and putting them back in via windows but I can't access Gparted either as it requires an admin login so like the others ... it just spins and spins.

Right now the updater says 11 packages need to be updated but when I click on it, the icon spins and spins and then just quits.  All programs requiring sudo or admin login do the same thing ... on BOTH logging in with my main id or with root under the GUI.

ANY suggestions would be most helpful as I'm really really really wanting to avoid a clean install ... AGAIN.  It's very time consuming just to get all of my settings back.  At least I finally bought he portable drive so most of my personal data files aren't lost.

IF I can get this fixed, I need to find a way to back up the system files every so often.  I tried "keep", a KDE program for just that but every time I ran it, it came up "folders restricted" which were the very folders I needed to back up so it was useless.

Regardless, if anyone can help get my admin/sudo access back or tell me a file that I might have inadvertently changed a setting to that might be causing the block, please please let me know!

---


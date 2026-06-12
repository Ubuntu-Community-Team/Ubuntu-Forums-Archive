---
title: "a very strange glitch"
date: 2020-09-13
forum: General Help
---

### Post by Skaperen on 2020-09-13
*edit:  the prefix should be Xubuntu, not Kubuntu.  sorry, and edit doesn't let me fix that.*

this afternoon, i renamed a username and its groupname and added about 7.5 GB of files to it.  i used commands **usermod** and **groupmod** to do this, among other things.  i renamed **user1009** to **gene**.  i looked at **/etc/passwd** and **/etc/group** and verified everything had worked OK.  then i ran **rsync** to copy about 93000 files to its home directory under its new name.  that worked OK.  it basically copied **/home/pdh** to **/home/gene** (the new name).  i then ran **chown -R gene:gene /home/gene** to set up the correct new ownership.  i ran **ls -l /home/gene** and it looked OK.  i did not check every single file.

then i modified the shortcuts file on all other users so that **Alt+G** would run **/usr/bin/dm-tool switch-to-user gene** to tell **lightdm** to switch to that user.  that is my method of switching between users.  it works.

i was able to successfully switch to user **gene** by pressing **Alt+G**.  i rebooted as a cheap way to get all users to load their shortcuts, again, alt it still worked.  then i paused to eat dinner.

when i was done with dinner i decided to do an upgrade.  for consistency i always reboot before the upgrade (so only admin is logged in) and reboot twice afterwards, so any steps that need to run after a reboot can and so my custom setup script has a fresh system to run from.

then i discovered that everything in /etc had reverted back to its original contents.  user **gene** did not exist, as far as this system knew.  i keep a directory of symlinks to user home directories in /homes because home directories are scattered around over 3 different file systems.  i had added the symlink for gene but it was now gone.  all the logs in /var/logs show there was never a user named gene.

but **/home/gene** _*still exists*_ and _*stlll*_ has the 7.5 GB of files i had copied with **rsync**.  all users still have the shortcut for **gene** which obviously won't do much good right now.

i was in the room the entire time, never leaving it for a second.  no one messed with the laptop (they are not allowed to unless i grant permission on a case by case basis).

other scans look like this afternoon never happened except that **last** does show the reboot i did this afternoon at about the right time.  logs show no I/O errors today and i saw no strange messages.

[I]any idea what might have done this besides an **invisible evil maid**?

any idea what i could check to see what caused this?[/I]

it looks like the entire root file system (about 64 GB and has **/**, **/etc**, and **/var**) reverted to an old copy while **/home** (about 900GB) did not.  i am running Xubuntu 18.04.5 LTS previously upgraded a few days ago.  file system types are all **ext4**.

---

### Post by TheFu on 2020-09-18
Two disks connected to the system?  Perhaps 1 was cloned from the other?

---


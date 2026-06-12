---
title: "Mounting from command line"
date: 2013-04-24
forum: General Help
---

### Post by Tralce on 2013-04-24
No, I don't mean using "mount /dev/sdxy /mnt/xxx". I've noticed that Xubuntu 12.10 does not automatically mount drives when they're plugged in the way Ubuntu does. In several cases with USB external hard drives, the icon for the drive will appear on the desktop and I will have to double click that. No big, but I'd like this to work in the terminal, as follows. 

I have two external drives I use heavily, labeled Zalman and 640GB. Ubuntu will automatically mount these in /media/tralce/Zalman and /media/tralce/640GB respectively, and so will Xubuntu if I click the icons. Several scripts I use depend on these drives being mounted in these locations. So what I'd like to do is somehow trigger Ubuntu's automatic filesystem mounting from the command line, OR from GUI, meaning I don't want to have to manually create mountpoints for these drives, and I don't want to do anything that will interfere with the GUI's automatic mounting. 

Any ideas?

---

### Post by r.stiltskin on 2013-04-24
Several things are not clear.

Are Ubuntu and Xubuntu on separate machines that both use those drives?  Or separate disks/partitions on the same machine?  Or something else?

Are you asking about Ubuntu or Xubuntu?

You say that you want to "trigger Ubuntu's automatic filesystem mounting", but Ubuntu automatically mounts the drives as soon as they are plugged in so there shouldn't be any need to do anything about that from the command line.

And if you're asking specifically about scripts running in Xubuntu where the drives aren't automatically mounted, why not add a few lines to the scripts to create 2 mountpoints, mount the drives, and then at the end of the script unmount and delete the mountpoints?

---


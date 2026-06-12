---
title: "[SOLVED] Help!...155 updates available!?"
date: 2007-03-12
forum: General Help
---

### Post by Cariboo1938 on 2007-03-12
Hi all,
once again I wrecked my system(Ubuntu 6.10-amd64). 
I wanted to install Python 2.5 and thought I have to un-install Python 2.4 first. 
This was a BIG mistake! After that, the system was reduced to very basic one with nothing as the "black screen terminal" running. 
Not knowing a better way to fix this, I installed from the live CD. 
Now the system is up again and the 'Update Manager" tells me that I can install 155 updates (240MB). 
Is this necessary or are there some I don't need?
Please, help? Thanks in advance for any reply, opinion or suggestion on that!

---

### Post by ComputerGuy56 on 2007-03-12
I installed all 155 updates in less then about an hour. I recommend that you would download the updates.

---

### Post by Kateikyoushi on 2007-03-12
I install all the updates every time, it does not make my system slower nor larger, and can always clean up. [LINK]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by Cariboo1938 on 2007-03-12
Thanks guys,
my problem is, that I'm on "dial-up" and this job takes about 40 hrs and it certainly slows down all other Internet activities. Therefore I try to minimize the amount of updates.

---

### Post by Kateikyoushi on 2007-03-12
In that case I would rather not upgrade just when a new version rolls out, downloading a CD every 6 months can be done, you could upgrade from the alternate install cd or make a /home partition and could resintall the system without loosing your settings.

---

### Post by Cariboo1938 on 2007-03-12
Thank you, Kateikyoushi,
so, you recommend to wait for Feisty Fawn (Ubuntu 7.04) rather than update Edgy...
Did I get it right??
I do have a /home partition and /Miscellaneous partition as well, which helped me already this time a lot.

---

### Post by Kateikyoushi on 2007-03-13
Right, I would rather wait than upgrade on dialup if everything works, that way you have to download only 2 cds a year and won't miss anything new.

---

### Post by _duncan_ on 2007-03-13
> **Cariboo1938 said:**
> Hi all,
once again I wrecked my system(Ubuntu 6.10-amd64). 
I wanted to install Python 2.5 and thought I have to un-install Python 2.4 first. 
This was a BIG mistake! After that, the system was reduced to very basic one with nothing as the "black screen terminal" running. 
Not knowing a better way to fix this, I installed from the live CD. 
Now the system is up again and the 'Update Manager" tells me that I can install 155 updates (240MB). 
Is this necessary or are there some I don't need?
Please, help? Thanks in advance for any reply, opinion or suggestion on that!

You don't have to update all 155 packages at the same time. For example, if you currently have 2 hours to update, click/unclick packages for update good for 2 hours worth of downloading. My rule of thumb for dial-up is 15 MBytes per hour. Repeat the process the next time you have time to download, until all updates are done. Ubuntu will work even if not all packages are fully-updated.

The tricky part is sometimes some packages have dependencies, so the total download may be larger than you have time for. In this case, I just cancel and review the list of packages for updating again until I hit a suitable size for the time available.

After you have fully updated the system, make sure to store the contents of the folder **/var/cache/apt/archives** somewhere else (e.g. another partition that will not be overwritten by a reinstall, a CD disc, flash drive, etc).

Later on, if you feel the need to reinstall Ubuntu, all you have to do is copy these files back into the same folder of the new installation.

The update manager will then make use of the .deb files in this folder, instead of downloading from the repo, saving 40 hours of downloading.

Added: BTW, I prefer using Synaptic over the Update Manager if there are a large number of packages to update. Synaptic allows you to display additional info on each package, including the download size. This is quite handy for the partial updating process I outlined above.

---

### Post by Cariboo1938 on 2008-01-05
> **_duncan_ said:**
> You don't have to update all 155 packages at the same time. For example, if you currently have 2 hours to update, click/unclick packages for update good for 2 hours worth of downloading. My rule of thumb for dial-up is 15 MBytes per hour. Repeat the process the next time you have time to download, until all updates are done. Ubuntu will work even if not all packages are fully-updated.

The tricky part is sometimes some packages have dependencies, so the total download may be larger than you have time for. In this case, I just cancel and review the list of packages for updating again until I hit a suitable size for the time available.

After you have fully updated the system, make sure to store the contents of the folder **/var/cache/apt/archives** somewhere else (e.g. another partition that will not be overwritten by a reinstall, a CD disc, flash drive, etc).

Later on, if you feel the need to reinstall Ubuntu, all you have to do is copy these files back into the same folder of the new installation.

The update manager will then make use of the .deb files in this folder, instead of downloading from the repo, saving 40 hours of downloading.

Added: BTW, I prefer using Synaptic over the Update Manager if there are a large number of packages to update. Synaptic allows you to display additional info on each package, including the download size. This is quite handy for the partial updating process I outlined above.

Thanks for your advice...this is a very reasonable strategy.....I'll remember that, because  I'll depend on DIAL-UP connection for a longer time.:)

---


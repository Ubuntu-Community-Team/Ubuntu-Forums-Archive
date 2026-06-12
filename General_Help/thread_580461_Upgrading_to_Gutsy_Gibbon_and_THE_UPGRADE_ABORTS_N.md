---
title: "Upgrading to Gutsy Gibbon and THE UPGRADE ABORTS NOW."
date: 2007-10-18
forum: General Help
---

### Post by awd-s on 2007-10-18
While running the distribution upgrade, the Upgrade Manager reports:

*"Not enough free disk space The upgrade aborts now. Please free at least 15.1M of disk space on /boot. Empty your Deleted Items folder and remove temporary packages of former installations using 'sudo apt-get clean'."*

Dutifully, you run 'sudo apt-get clean' from the command line, re-invoke the Upgrade Manager only to receive the same informative message such that instead of being Gutsy you become a Gibbering gibbon.

Your problem is, most likely, caused by your disk drive being clogged by dozens of obsolete Linux Kernels that remain undeleted after every kernel upgrade.

You solve this problem by opening the Synaptic Package Manager then executing a search for ***linux-image***.

Next, select each older kernel for complete removal, along with its associated file.

Apply the change and wait for Synaptic to release the disk space.

Finally, return to the Upgrade Manager and perform the distribution upgrade. All should be well, though it may take time as the servers seem overloaded by tens of thousand of people feverishly downloading the new release.

---

### Post by Velociraptor on 2007-10-20
Not quite knowing where to find the Synaptic Package Manager, you blunder your way through the menus and get lucky: System -> Administration -> Synaptic Package Manager

Frustrated that searching for **linux-kernel **brings almost no results, you try for **linux-image** instead. And things look a lot better.

BTW, thanks for the fix!  It's weird, I had already manually deleted those old kernel files from /boot. So deleting them from the Synaptic Package Manager actually freed *no* space on /boot. But it stopped the /boot error message on upgrade. Duh.

---

### Post by awd-s on 2007-10-22
Thanks for catching my mistake -- **linux-image** it is. I'll correct my original.

---


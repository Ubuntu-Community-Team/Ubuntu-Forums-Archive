---
title: "Clone OS Partition to Smaller SSD"
date: 2018-11-17
forum: General Help
---

### Post by cliffflip on 2018-11-17
Hi, I have 18.10 installed on my WDC Blue (1TB), and I want to clone the OS partition to 120GB SSD. Space used for installation and other data is _+_ 60GB.
Is it possible to clone partition to smaller drive? If so please describe the easiest steps on how to do that.
I cloned OS partition in Windows a few times but never in Ubuntu yet. Thanks in advance :)

---

### Post by HermanAB on 2018-11-17
Yes, it is possible.  

However, it only takes about 20 minutes to install the latest version of Linux from scratch, so cloning an old version is a terrible waste of time.  In the 57 minutes since posting your question, you could have installed three machines already...

---

### Post by TheFu on 2018-11-17
You cannot "clone" something to a smaller drive.  A "clone" would be 100% bit-for-bit copy of the entire disk.

But you can use **fsarchiver** to backup a larger partition and restore it into a manually created smaller (or larger) partition, but the UUIDs for the partitions will likely change, so be prepared to fix the fstab using a live-boot flash/DVD Linux disc and reinstall grub on the new disk.  There are guides which explain these thing at help.ubuntu.com,  but you'll need to be very flexible since none of those guides will explain exactly what you need to type.  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) is the fstab entry.
Google found these for Grub:
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://www.tecmint.com/rescue-repair-and-reinstall-grub-boot-loader-in-ubuntu/](https://www.tecmint.com/rescue-repair-and-reinstall-grub-boot-loader-in-ubuntu/)

Or do like Herman suggests with just a little more effort, which might be easier for people uncomfortable with the shell, by backing up your $HOME and the list of manually installed packages, then do a fresh install (15 min), restore your personal data from $HOME, and finally take the list of previously installed packages and re-install all of them at once.  There's a backup tool called **aptik** which should make this easier for normal desktop users.  I don't know if it works on 18.10. It probably does. [http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/](http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/)

---

### Post by cliffflip on 2018-11-17
Thanks for the replies :)]

> **HermanAB said:**
> Yes, it is possible.  

However, it only takes about 20 minutes to install the latest version of Linux from scratch, so cloning an old version is a terrible waste of time.  In the 57 minutes since posting your question, you could have installed three machines already...

I don't want to set everything else from the scratch (apps, preferences, etc), 
especially I'm using this PC for media server (Plex). Scanning and downloading metadatas could take hours.

> **TheFu said:**
> You cannot "clone" something to a smaller drive.  A "clone" would be 100% bit-for-bit copy of the entire disk.

But you can use **fsarchiver** to backup a larger partition and restore it into a manually created smaller (or larger) partition, but the UUIDs for the partitions will likely change, so be prepared to fix the fstab using a live-boot flash/DVD Linux disc and reinstall grub on the new disk.  There are guides which explain these thing at help.ubuntu.com,  but you'll need to be very flexible since none of those guides will explain exactly what you need to type.  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) is the fstab entry.
Google found these for Grub:
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://www.tecmint.com/rescue-repair-and-reinstall-grub-boot-loader-in-ubuntu/](https://www.tecmint.com/rescue-repair-and-reinstall-grub-boot-loader-in-ubuntu/)

Or do like Herman suggests with just a little more effort, which might be easier for people uncomfortable with the shell, by backing up your $HOME and the list of manually installed packages, then do a fresh install (15 min), restore your personal data from $HOME, and finally take the list of previously installed packages and re-install all of them at once.  There's a backup tool called **aptik** which should make this easier for normal desktop users.  I don't know if it works on 18.10. It probably does. [http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/](http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/)

thank you for the tutorial, I'll look into it and will report back

---

### Post by HermanAB on 2018-11-17
Backup your data, use apt to get a list of installed packages and save it.  Install from scratch, then run apt with the list of packages to install what is missing, then get your data from backup.

---

### Post by TheFu on 2018-11-17
I run a plex server too.  If I were trying to move that install to a different system, I'd
* Make a list of manually installed packages using apt-mark, save that list to my HOME
* Perform a fresh install onto the new disk
* Connect the old OS disk to the new system install
* Selectively rsync /var/lib/plex* from the old to the new
* Copy everything from HOME from the old to the new <---- the old HOME to the new HOME
* Reinstall the packages from the list.  There's a way to take the list from apt-mark and tell the pkg manager to install all those things.
* Lastly, I'd install the exact same Plex version that I had running.  I never run the latest and install from a .deb file, just that single package.  WAF demands that plex work, always, unless I beg for downtime in advance.  Weekly patching is ok, but anything over 15 minutes can cause family issues. ;)  Fortunately, hardware failures are forgiven, though data loss is not.

---


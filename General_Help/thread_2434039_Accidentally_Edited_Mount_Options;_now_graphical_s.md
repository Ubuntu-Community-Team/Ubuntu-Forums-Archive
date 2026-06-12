---
title: "Accidentally Edited Mount Options; now graphical shell doesn't load"
date: 2019-12-29
forum: General Help
---

### Post by saintsfan342000 on 2019-12-29
Hello,

TL;DR:  I poked around in Gnome Disks Utility and messed up the Mount options.  Now only a CLI launches when I boot my computer. How can I restore the normal boot up?


I was attempting to do something to an external drive using the [Gnome Disks Utility]("https://wiki.gnome.org/Apps/Disks").  I inadvertently Edited Mount Options on my PC hard drive, similar to [how it's described here]("https://www.techrepublic.com/article/how-to-edit-linux-drive-mount-point-options-using-a-gui/").  I am not totally sure what I did, but I definitely turned "Automatic Mount Options" ON (for which I had to enter my password) and turned it off (for which I also had to enter my password). I am unsure if I did these to the same partitions....I recall seeing some start get added to each partition.

The Lubuntu GUI will not load anymore.  Startup goes normally, then this screen shows:
[IMG]https://i.imgur.com/leJeTsf.jpg[/IMG]

After some time on that screen, I am prompted can log in in CLI.  After doing so I start in my usual home directory, but none of the typical directories, e.g. Desktop, are present.

I also tried launching in recovery mode.  Similar story in that I can I am only given a CLI to log in, but doing so here the typical directories are present, as are all the files I would expect to see.

I am happy to provide output from any files, documents, etc. that you need to help resolve.  Thank you so very much to anyone who is willing and able to help out.

---

### Post by oldfred on 2019-12-29
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by saintsfan342000 on 2019-12-29
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Thank you.  I cannot apt-add-repository.  I get an error:
```
FileNotFoundError:  [Errno 2] No usable temporary directory found in ['/tmp', 'var/tmp', '/root'].
```

Unless you tell me otherwise, I will attempt the Boot-Repair ISO.  Thanks again.

UPDATE:  My BIOS will not recognize a USB device from which I can boot.  I need to obtain a blank CD/DVD and write Boot-Repair to it.  Not sure if I have any on hand.

---

### Post by saintsfan342000 on 2019-12-30
[**Method #1 **of the accepted answer]("https://askubuntu.com/a/435966/429950") fixed the issue for me.  My computer and operating system now boot normally.

---

### Post by TheFu on 2019-12-30
Boot from the flash drive used to install Lubuntu.  Go into "Try Lubuntu" mode, use that to edit the /etc/fstab file to fix the issues.
The easy way would be to restore that file from a backup PRE-screwing around.

We've all been in a similar situation - i.e. ooops, broke something, need to fix it.  The issue is in the fstab file.  I won't guess what it might be.  

I seriously doubt boot-repair will help anything.

---


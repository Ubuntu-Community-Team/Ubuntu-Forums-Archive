---
title: "boot eror &quot;ALERT ! does not exist. Droping to a shell!&quot;"
date: 2007-05-14
forum: General Help
---

### Post by AidanPM on 2007-05-14
i have gotten this twice...
[IMG]http://img249.imageshack.us/img249/8038/wubimediumsw7.jpg[/IMG]
The first time I thought I screwed something up in windows. But the second time it happened the only thing I did differently before it gave me this message was a hard reset(cut the power to my box) of my computer. And the more I thought about it, I realized that the manual reset was the only thing the two incidences have in common.

The first time I didn't know what to do and I figured I didn't have too much to lose so I just reinstalled. But this time I have everything customized to the MAX and I don't want to lose anything. So is there anything I can do to make it go back to normal, without reinstalling?

---

### Post by ago on 2007-05-14
Can you provide more descriptive info? Did you have an installation of wubi working to begin with? And it did not work after a hard reboot? Of windows or of Linux?

---

### Post by AidanPM on 2007-05-14
ya i had Wubi successfully install and working two different times(it's really great). And the manual resets were done in Ubuntu.

---

### Post by ago on 2007-05-14
With hard resets you might have corrupted the ntfs files and/or the ext3 filesystem inside the ntfs file. Not sure what the procedure is for ntfs checking, but for linux you have to run fsck.ext3. You can boot with a live CD and run fsck on the virtual disk files. As for your settings they should be on home.virtual.disk and you can simply back that up (copy it somewhere else), then see if it works on a new installation as it is, and if it doesn't run fsck.ext3 on the file (this is assuming that any ntfs problems have also been fixed).

---

### Post by AidanPM on 2007-05-14
Thanks for the advice. but when I restarted my computer to get into a live season with my Ubuntu 7.04 disk I just walked away from my computer and forgot to start Ubuntu from the disk. So by default it loaded into Wubi Boot-loader and it started up fine.  To make sure it did this without the Ubuntu disk in the drive I removed the disk then rebooted. After all that Ubuntu is starting normally all on it's own. Go figure.

---


---
title: "gedit warning message when saving"
date: 2007-04-08
forum: General Help
---

### Post by newblacknoise on 2007-04-08
hi there.

I re-installed 6.10 this morning (lots of screen resolution headaches - don't ask, long story), and everything has been behaving itself since then, except for one thing.

Gedit seems to have trouble when I try saving a text file that I've been working on. It won't happen every time, but 2 times out 3 when I attempt to save the file I will get a message stating:

Could not create a backup file while saving [filename]
gedit could not backup the old copy of the file before saving the new one. You can ignore this warning and save the file anyway, but if an error occurs while saving, you could lose the old copy of the file. Save anyway?

I can then choose 'Save Anyway' or 'Don't Save'. Selecting 'Save Anyway' seems to work, and the file is successfully saved, but I don't like the implication of losing my work, and plus, the message is kind of annoying!

I can't think of any good reason why this would start, but the only thing slightly out of the ordinary is the path the files is accessed by a symbolic link. So rather than being in my home folder, as gedit seems to think, it's a link pointing to another directory on another partition.

thanks.

EDIT: ok, I tried loading the files from their direct path, rather than through the symbolic link, and it's still giving me warnings.

---

### Post by FakeOutdoorsman on 2007-04-08
I get this message when I try to save to my FAT drive that I use to share data between Ubuntu and Adobe Software Compatibility OS (aka Windows).

---

### Post by newblacknoise on 2007-04-08
that's the same setup i'm using: a FAT32 partition to share data between windows and ubuntu.

do you get this error just with gedit, or with other programs too?
for the moment, my problems are just with gedit. other text editors (which i've been using in the meantime) seem to behave just fine.

---

### Post by strabes on 2007-04-08
Just disable the creation of backup files when saving. You can do that in the behavior section of the gedit preferences I believe.

---

### Post by newblacknoise on 2007-04-08
well, i tried to turn off the option 'create backup copy of files before saving' in the gedit preferences, but to no avail.

now, the error message simply specifies that it cannot create a *temporary* backup file before saving.

i appreciate the help though!

---

### Post by FakeOutdoorsman on 2007-04-09
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/gedit/+bug/69184](https://launchpad.net/gedit/+bug/69184) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **newblacknoise said:**
> do you get this error just with gedit, or with other programs too?
for the moment, my problems are just with gedit. other text editors (which i've been using in the meantime) seem to behave just fine.

Just gedit.  This is a gedit bug that has been submitted to Launchpad
[Bug #69184: "Could not create a backup file" when trying to save a file in a VFAT partition]("https://launchpad.net/gedit/+bug/69184")

Constantine Evans suggests this fix in the bug report:
*For now, you can get around the issue by mounting with the option uid=(YOUR_USER_NUMBER) instead of uid=000 (probably uid=1000).*

He refers to the fstab entry.  To find out your user id (uid) you can type **id** in terminal or open System -> Administration -> Users and Groups -> Select your user -> Properties -> Advanced. You can edit fstab with the following:

```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

I haven't tested to see if it works.

---

### Post by newblacknoise on 2007-04-09
hey, thanks for the tip FakeOutdoorsman!

it worked like magic (oooo, eerie). i haven't run it through any rigourous testing, but so far gedit is behaving like the happy little text editor it should. i guess i assumed it was something strange with my installation, or that i'd messed something up when screwing around with settings. i never thought to check the bug list.

thanks again.

---

### Post by CrownP10:8 on 2007-07-06
I too had this problem when working on files on a VFAT partition. The solution was to modify /etc/fstab to mount that partition under my user's ownership; perhaps this should be default for VFAT setup in Ubuntu?

```
# Entry for /dev/sda2 :
UUID=BD91-0106 /share vfat user,auto,fmask=0111,dmask=0000,uid=1000,gid=1000 0 0
```

After making the change in /etc/fstab I unmounted and remounted the partition with:

```
sudo umount /share
sudo mount -a
```

---


---
title: "Ubuntu Stuck On Loading Screen"
date: 2013-06-25
forum: General Help
---

### Post by elfin8er on 2013-06-25
A couple days ago, I was on Ubuntu, and the nav bars of all of windows disappeared. It had happened a couple of times before, and restarting always fixed it, so I restarted as usual. How ever, Ubuntu didn't restart, and is now stuck on the Ubuntu loading screen. It says Ubuntu, with three orange dots indicating it has loaded all the way. I tried letting it go over night, but it still didn't load. Any suggestions?

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]elfin8er; Hi !

I can think of 2 things one needs to do in this situation.
1. On some versions of 'buntu with the liveDVD there is an option "boot from hard disk"; available from the boot options screen (shift key @ plymouth screen ->language screen, escape key to accept default -> boot options screen). What results from this boot method ?

2. Run a file system check:
[/COLOR]#From liveDVD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
[COLOR=#000000]```
sudo blkid ## to identify your partitions

```[/COLOR]```
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```
[INDENT=2]
please to advise on results. -> just try'n to help


[/INDENT]

---

### Post by Ranko Kohime on 2013-06-25
I had this same thing happen, (not the errors, but the failure to boot up) after Ubuntu tried an automatic distro upgrade from 12.10 to 13.04.  Is the loading screen showing a different release version than you had installed?

---

### Post by elfin8er on 2013-06-25
> **Bashing-om said:**
> [COLOR=#000000]elfin8er; Hi !

I can think of 2 things one needs to do in this situation.
1. On some versions of 'buntu with the liveDVD there is an option "boot from hard disk"; available from the boot options screen (shift key @ plymouth screen ->language screen, escape key to accept default -> boot options screen). What results from this boot method ?

2. Run a file system check:
[/COLOR]#From liveDVD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
[COLOR=#000000]```
sudo blkid ## to identify your partitions

```[/COLOR]```
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```
[INDENT=2]
please to advise on results. -> just try'n to help


[/INDENT]

Not sure what the Plymouth screen is.

---

### Post by Bashing-om on 2013-06-25
elfin8er;
Booting into the live Medium:
Sorry not to be specific. The "plymouth screen is that first colored screen after the booting process has started ...
In your case, as soon as the bios screen clears, depress and hold the shift key ... and one goes directly to the language screen, and will not even see the plymouth screen; and the escape key then results in the boot options screen.
edit: one must of course have the boot device's priority set as 1st boot priority in bios setup.

[INDENT][INDENT]hope this helps[/INDENT][/INDENT]

---

### Post by Ranko Kohime on 2013-06-25
Plymouth shows the Ubuntu logo on startup.

---


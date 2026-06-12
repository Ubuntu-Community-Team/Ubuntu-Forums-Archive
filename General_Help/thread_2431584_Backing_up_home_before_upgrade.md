---
title: "Backing up home before upgrade"
date: 2019-11-18
forum: General Help
---

### Post by roundrock90210 on 2019-11-18
I am running Kubuntu 14.04. I want to upgrade to the newest LTS which looks like I will need to go from 14.04 to 16.04 to 18.04. I would like to do a one time backup of my home drive. I did the du command and it says it is about 43GB. I was going to buy a thumb drive of 64GB. I'm sure my comp doesn't have a USB 3.0 port. Should I just tar the home directory to the thumb drive or do something different like rsync? I don't need to backup the programs or the OS itself. Most of my searches come up for everyday backup. I have certain directories that I backup regularly.

---

### Post by CatKiller on 2019-11-18
Either approach should be fine.

I will say, though, that you would be better off doing a fresh install of 18.04.

The 14.04 repositories are long gone, so starting the upgrade process would be a pain. For Kubuntu specifically, I believe there was a bug that prevented going from 14.04 to 16.04. Each upgrade stage takes a couple of hours as each package needs to be downloaded, installed, and configured, and you may have used PPAs or odd configurations that could cause it to fail.

By contrast, a fresh install takes about 20 minutes.

---

### Post by roundrock90210 on 2019-11-18
I've always done the upgrades through the internet. Can you install 18.04 while keeping the /home/username/ drive with DVD or should I just back it up, then use a DVD to do a fresh install to 18.04 then unzip my home drive that I backed up? Probably makes sense as it would take hours to go from 14.04 to 16.04 to 18.04. I do get the notice to do the upgrade to 16.04 anytime I reboot.

---

### Post by CatKiller on 2019-11-18
If you've got /home as a separate partition you can leave it untouched with the installer (which is why people do that). If it's all on one partition then you can't. Using tar or rsync to duplicate your Home folder and then copy it back afterwards would be functionally equivalent to having /home on a separate partition.

You used to be able to use the install image as a local repository to upgrade in place, but I don't know if you still can, and you'd still have to go through each release's installing/configuring/next package routine. A completely fresh install would be quicker and easier.

---

### Post by roundrock90210 on 2019-11-18
Okay, thanks for the help! I have everything on one partition.

---

### Post by TheFu on 2019-11-19
While you can use rsync, it needs a Unix target file system to work properly and retain directory and file permissions.  Those are 50% of the required information in a backup.  Do not use exFAT, FAT32 or NTFS on the backup storage.

If you have a native Linux file system on the backup storage, the options are much greater and you can use a real backup tool that does efficient versioning.
```
sudo rsync -avz /home /mnt/backup-storage/
```
or
```
sudo rdiff-backup --exclude-special-files  /home /mnt/backup-storage/
```
if you use the 2nd command above, perhaps weekly, then you'll have a new version added and it will only backup newer stuff.  rsync and rdiff-backup work in very similar ways.  Both effectively make a mirror of the most recent run.  rdiff-backup keeps the last backup as a mirror, which all prior versions as diffs.gz files. This is crazy efficient. It also means that at some point, really old versions need to be removed and removing intermediate versions isn't allowed.
Both rsync and rdiff-backup have options to limit/exclude files by name, size, date, .... Backing up 20 versions of a 12GB movie isn't exactly useful.
Both of these tools need native linux file systems on the target. Don't use them if that isn't your situation.

If you can't or won't format the target backup storage, then the tools to be used have to retain the owner, group, permissions and ACLs some other way.  duplicity will do that, but it works like a backup tool from 1970.
```
S M T W T F S
- &#8211; - &#8211; - &#8211; - 
D D D D D D M
D D D D D D F
D D D D D D F
D D D D D D F
```
D = incremental
F = Full
M = Monthly-Full, retained

I've been using rdiff-backup since around 2010. The first backup is like an rsync and takes that long.  Every backup version after that is only change data, usually 1-4 minutes total.  It isn't a hassle. It will change your life around backups. They aren't a big deal and you'll have a recent version so any data loss issues are minor inconveniences only.

I should mention that all these tools support network-based backups.  I "pull" the backups and the client machines don't have direct access in any way to the backup storage. This provides the best protection against crypto-malware, in addition to all the other 1001 things that having good, versioned, backups can provide.

---

### Post by roundrock90210 on 2019-11-19
I'm going to pickup a USB just to do the upgrade and then use it for other things when done. I'm just worried the .kde files on the home drive backup will mess up my clean install. Idk, maybe I'll go with Ubuntu instead of Kubuntu. I haven't been following the GUIs lately.

---

### Post by TheFu on 2019-11-19
> **roundrock90210 said:**
> I'm going to pickup a USB just to do the upgrade and then use it for other things when done. I'm just worried the .kde files on the home drive backup will mess up my clean install. Idk, maybe I'll go with Ubuntu instead of Kubuntu. I haven't been following the GUIs lately.

Regardless of the drive you get, you'll want to use a native Linux file system.  ext4 if spinning or SSD and f2fs if a flash drive.  f2fs needs f2fs-tools package installed.  Do not use FAT-whatever or NTFS.  

Config file settings change from release to release, so there is always a concern with keeping those files around.  Ideally, when the new KDE runs, if it sees any incompatible or changed settings, those should be corrected for the new settings.  Unfortunately, we don't live in an ideal world.  The same applies to every GUI and GUI program.  I would risk it and pull everything back in the new install.  But if any program seems to be misbehaved, create a new account and see if that program still misbehaves or not.  If it doesn't, then the older settings are the most likely problem.

---

### Post by CatKiller on 2019-11-19
> **roundrock90210 said:**
>  I'm just worried the .kde files on the home drive backup will mess up my clean install. Idk, maybe I'll go with Ubuntu instead of Kubuntu. I haven't been following the GUIs lately.
That concern would make me do the opposite: the KDE devs know about old KDE releases, and any changes to configuration format they're going to do their best to keep backwards-compatible or convert to the new format. Gnome devs, by contrast, don't care at all about any KDE version, past or present. 

For the practical restoring-settings step I would just copy everything from the old Home folder into the new one as a first step. If that causes any issues, then try deleting particular settings folders to have them recreated from defaults.

---

### Post by guiverc on 2019-11-19
I didn't read all the history, but you can upgrade from one release to another, without loosing your user data in /home even if a single partition is used.  Use the 'something else' option, select your current partition(s) [*one in your case*] and ensure you don't have format ticked.  That will cause your installed (*post-install*) software-packages to be noted, system directories wiped, system installed, then software-packages you'd added to be re-installed (if available for new release) all without touching /home or any user data/setting (providing you don't have format ticked).  You can get an error if any packages can't be found (which is possible; you just note any programs if you need them & re-install manually), but this error can 'worry' nervous-users but it's no problem.

This method is not as clean, some problems from the prior release (if in user settings) will thus survive to new system, but that'll happen anyway if you restore data. I use it often.  Backups should of course still be done.  This method allows you to skip releases, even go backwards (to an earlier release) though problems can occur this way if you've used later features in programs that earlier versions of programs don't know how to cope with in your *data* files (ie. program specific problems), and you can use it with the same release too.

---


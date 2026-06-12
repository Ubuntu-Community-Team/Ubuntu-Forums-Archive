---
title: "I made /home a new partition, but.."
date: 2008-02-09
forum: General Help
---

### Post by NHansen on 2008-02-09
So I followed this guide: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome") and made /home it's own partition.
Everything went well, except when I booted up, none of my settings are here. None of my sessions, desktop effects, firefox bookmarks, nothing.

anyone know what this could be?

---

### Post by taurus on 2008-02-09
Did you remember to modify /etc/fstab and add an entry for that partition, mounting it to /home?

Post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by NHansen on 2008-02-09
it's mounted, and ubuntu recognizes it as home... it's just that my settings arent there.
this guy had the same exact problem, but they didnt seem to resolve the issue
[http://ubuntuforums.org/showthread.php?t=613690]("http://ubuntuforums.org/showthread.php?t=613690")

---

### Post by NHansen on 2008-02-09
```

cat /etc/fstab



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=967f870e-59f5-4fab-901e-5c22355acbbb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=2d6df12e-94a1-45ef-8e4e-ed8a33210c88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda7 /home ext3 nodev,nosuid 0 2




df -h


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             100G   91G  5.4G  95% /
varrun                982M  284K  982M   1% /var/run
varlock               982M     0  982M   0% /var/lock
udev                  982M   80K  982M   1% /dev
devshm                982M     0  982M   0% /dev/shm
lrm                   982M   34M  948M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda7             189G   51G  128G  29% /home
/dev/scd0             696M  696M     0 100% /media/cdrom0
/dev/sdb1             970M  702M  269M  73% /media/LINUX


```

---

### Post by taurus on 2008-02-09
Personally, I would make the last line in your /etc/fstab to look like this instead.

```
/dev/sda7   /home   ext3   defaults   0   2
```
Did you copy over all those hidden directories, the ones start with the . in front?

```
ls -la ~
```

---

### Post by DoktorSeven on 2008-02-09
Do you have permissions on your /home/[username] files?  Do a 
```
ls -l /home/yourusernamehere/
```
and make sure the third column has your username:
```
drwx------ 2 YOURUSERNAMEHERE users 4096 2008-02-08 12:23 Desktop
```
...as an example (timestamps might be slightly different).  If it doesn't, that might be your issue.

The guide you linked to used an unusual method for copying files (cpio) where I would use the more complete **cp -dpR /old/home/youruser/ /new/**, which properly preserves permissions, dotfiles/directories and symlinks, where I'm not certain cpio would.

If this has happened, you can get it back with:
```
sudo chown -R YOURUSERNAMEHERE /home/YOURUSERNAMEHERE
```

If it didn't copy over the dotfiles (all the "hidden" files), you may need to recopy the files using **cp** (as in my example) instead of the command they gave.

---

### Post by NHansen on 2008-02-09
Yes, it copied all the .files and folders
Yes, I have all permissions (username in both 2nd and 3rd columns)

---

### Post by NHansen on 2008-02-09
hmm, I don't understand what's wrong.
I mean, my home is the same as my home_backup, which should mean there should be absolutely no change, right?
:-k

---

### Post by NHansen on 2008-02-09
hmm, something weird I've noticed:
as I am setting up my Avant Window Manager again, I noticed it's keeping the settings for the application Launcher icons, and little things like that.
I figure I will just redo my settings, but now I just want to make sure I can delete my home_backup

---

### Post by NHansen on 2008-02-09
ok so I just rebooted and got this error when logging back in:

"User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

It didn't seem to affect anything, though... but what do I do about that?
Would this be appropriate(found on another thread)?
```

sudo chmod 644 /home/nicolas/.dmrc
sudo chown ricardisimo /home/nicolas/.dmrc
sudo chmod -R 700 /home/nicolas
sudo chown -R ricardisimo /home/nicolas

```

edit: that worked :)

---

### Post by taurus on 2008-02-09
> **NHansen said:**
> ok so I just rebooted and got this error when logging back in:

"User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

It didn't seem to affect anything, though... but what do I do about that?
Would this be appropriate(found on another thread)?
```

sudo chmod 644 /home/nicolas/.dmrc
**[COLOR="Blue"]sudo chown ricardisimo /home/nicolas/.dmrc[/COLOR]**
sudo chmod -R 700 /home/nicolas
**[COLOR="Blue"]sudo chown -R ricardisimo /home/nicolas[/COLOR]**

```

edit: that worked :)

Your login name is nicolas, _NOT_ ricardisimo!

```
sudo chown -R nicolas /home/nicolas
```

---

### Post by NHansen on 2008-02-09
oh, yeah, hehe. I changed that in the terminal when I saw it
thanks

---


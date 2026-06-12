---
title: "Backup."
date: 2020-05-03
forum: General Help
---

### Post by Hewjr100 on 2020-05-03
I used Backup to create a USB of Ubuntu 20.04.  I included Home and /Opt.  So I did a fresh install and did a restore, everything was fine except that the following apps were not in the backup:

gnome-tweak-tool lm-sensors gparted dconf-editor bleachbit terminator chrome-gnome-shell brasero ubuntu-restricted-extras vlc gufw.

What folder are they in so I can create another image with them.  Another file I need is grub, but when I go to /etc/default/grub, grub is greyed out.

Henry

---

### Post by rbmorse on 2020-05-03
There was a post here not too long ago from user Thefu describing the correct way to do this using apt-mark.  Damned if I can find it, but perhaps he, or someone else, can post a pointer.

---

### Post by TheFu on 2020-05-03
/home and /opt don't have any applications, usually.  I don't backup any installed packages, just the list of manually installed packages, so those can be reinstalled later.  I haven't tested this on 20.04 and snap packages wouldn't be included but the normal APT installed stuff will work:

```
$ apt-mark showmanual | tee $local_backup/pkgs_manual.lst
```

To restore, use:
```
$ sudo apt-mark manual $(cat pkgs_manual.lst)
$ sudo apt-get -u dselect-upgrade
```

Then I think **sudo apt-get install -f** is needed. I know it works, but haven't restored EVERYTHING in a while.  Usually my restores are just a file or directory or DBMS data file.

The trick is to include the pkgs_manual.lst file (name it whatever you want) in your backups.  Then bring that over to the new machine and restore using that list.

Oh - sorry about using variables.  My backup script(s) are all perl, so the $local_backup is a perl scalar ... just like a normal bash text variable for something like this.

---

### Post by Hewjr100 on 2020-05-03
Will look into it, and give it a try.

Henry

---


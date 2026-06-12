---
title: "No gui"
date: 2007-10-20
forum: General Help
---

### Post by schreck494 on 2007-10-20
When I upgraded to Gutsy, I was trying out a different driver for my video card since things weren't as smooth as they used to be.  I have a Radeon 7000 Mobility and it was set to the Radeon driver.  I switched it to the Radeon(VESA) driver, and now when I turn on my computer, it goes through all of the normal boot stuff, so I see the Ubuntu boot screen and everything, but once you get to the point where you should get the login screen, I just get a text login.  What should I do?

---

### Post by DagMan on 2007-10-21
login with username and password.
sudo /etc/init.d/gdm restart
and if not that then
startx
and if not that then
/usr/bin/startx /usr/bin/gnome-session

However is sort of sounds like you might have wrong settings in your xorg.conf file and if that's the case then none of that will work.  If none of that works, look in /etc/X11/ to see if there was a backup of xorg.conf you can copy over.  and if not, boot back into the live CD, mount the root partition, and copy the xorg.conf file that the CD makes in RAM to the appropriate loacation on the disk.

---

### Post by schreck494 on 2007-10-21
I think that you are right that it is a messed up config file.  When I run the startx command, I get three errors.
Failed to load module "type1" (module does not exist,0)
VESA(0): No valid modes
Screen(s) found, but none have a usable configuration

So how do I check for a backup config file and revert to that file?

---

### Post by DagMan on 2007-10-21
```
ls /etc/X11/xorg*
```
and you will see 
/etc/X11/xorg.conf 
which is the file it's currently trying to use.  If you see other ones like
/etc/X11/xorg.conf-backup
/etc/X11/xorg.conf~
or such then try copying it over
...well first backup the current one, although it isn't working, but still back it up
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backed-up-file
```
and to restore it you would do this 
```
sudo cp /etc/X11/xorg.conf-backed-up-file /etc/X11/xorg.conf
```

then you can try, assuming there is a backed up file there, copying the backup into place where name-of-file-to-use is the file.
```
sudo cp /etc/X11/name-of-file-to-use /etc/X11/xorg.conf
```





To do the thing I suggested with using the live CD, you would boot into it then mount the partition that the main part of the install is on.  This is the / or also called root partition.  And then you could copy the file that the live CD wrote to RAM to use to the partition on the hard drive you mounted.
If your hard drive partition is the first one on the disk, and this would be if Ubuntu is the only thing there, then it would look like this in a terminal.
```
sudo mount /dev/sda1 /mnt
sudo cp /etc/X11/xorg.conf /mnt/etc/X11/xorg.conf
```

But if you are sharing a windows install where windows is the first partition and ubuntu's install started on the second partition it would be this
```
sudo mount /dev/sda2 /mnt
sudo cp /etc/X11/xorg.conf /mnt/etc/X11/xorg.conf
```

And if windows had 2 partitions then ubuntu it would be this
```
sudo mount /dev/sda3 /mnt
sudo cp /etc/X11/xorg.conf /mnt/etc/X11/xorg.conf
```

But if you have more than one drive and ubuntu is on the second drive then like this
```
sudo mount /dev/sdb1 /mnt
sudo cp /etc/X11/xorg.conf /mnt/etc/X11/xorg.conf
```

you can see in the above 4 things that hard drive partition number is at the end /dev/sda**X**
where X is the partition number, and then in the last one with the install on the second hard drive, the last letter there is the drive, /dev/sda being the first drive and /dev/sdb being the second and then followed by a partition number.  So in the last thing above it's mounting the first partition of the second drive... assuming that's what you use.  This isn't important except that you feel a little better about what you're mounting though if you mount the wrong one it can't really hurt it because you'de be presumably copying to a directory that doesn't exist and it would fail.

Good luck.  I hope something works.

---

### Post by schreck494 on 2007-10-21
Restoring the xorg config file worked.  Thanks for all your help.

---


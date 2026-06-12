---
title: "HELP. gnome session won't start!"
date: 2007-01-27
forum: General Help
---

### Post by billybag on 2007-01-27
after logging in i get this:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions tosee if you can fix this problem.

[ ] View details (~/.xsession-errors file)

/etc/gdm/PreSession/Default: Registering your session with wtmo and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "billy"
/etc/gdm/Xsession: Beginning session setup...
mkdtmp: private socket dir: Permission denied


HELP

---

### Post by taurus on 2007-01-27
Boot into recovery mode from GRUB menu and run

```
aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
(replace **username** with your login name)
df -h
```

Paste the output of the last command here.

---

### Post by billybag on 2007-01-27
it wouldnt let me remove any of the directories from the trash

File System         Size    Used    Avail       Use%      Mounted On
/dev/hdb1           75G    64G     6.7G       91%        /
varrun                126m 112k     125m      1%          /vaqr/run
varlock               126m  4.0k     126m     1%          /var/lock
procbususb        10m     168k    9.9m     2%         /proc/bus/usb
udev                  10m     168k    9.9m    2%         /dev
devshm              126m     0      126m    0%         /dev/shm
irm                    126m      18m  108m   15%       /lib/modules/2.6.17-10-i386/volatile

---

### Post by billybag on 2007-01-27
i just used -r and that got rid of directories

---

### Post by taurus on 2007-01-27
You have 75GB and you've filled it up with only 6.7GB left!  What did you download anyway?  Now, you should be able to log in with your regular account so you should take a look in $HOME to see if there is something you don't need, remove it since it's just taking up space.  You can see how much your $HOME account is taking up with this command from a terminal.

Applications -> Accessories -> Terminal
```
du -h ~
```

---

### Post by billybag on 2007-01-27
i am still having trouble logging in. i DLed VMWare server. that must have been the icing on the cake

---

### Post by billybag on 2007-01-27
i still cant get it to work and i keep removing directorys that i know have a lot of stuff in them like my shared folders and completed torrents folders

---

### Post by billybag on 2007-01-27
so i am now only using 55G out of 75 and still no luck!!!

---

### Post by billybag on 2007-01-27
should i reinstall ubuntu-desktop package?

---

### Post by billybag on 2007-01-27
please contact your system administrator to resolve the following problem: could not open or create the file "(null)"; this indicates there may be a problem with your configuration, as many programs will need to create files in your home directory. the error was "failed to create file /tmp/gconf-test-locking-file-1TQQMT': permission denied" (errno=2)....

---


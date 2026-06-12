---
title: "System crash causing problems"
date: 2007-05-04
forum: General Help
---

### Post by forchessonly on 2007-05-04
I have ubuntu 6.06 installed on an external usb drive, accidentally it got shutoff while downloading. I rebooted and all of a sudden I don't have sound and my windows partitions are unreadable. It says the drive or partitions can't be mounted, something about no fstab entry in the mtab. It also claims that I don't have sound installed anymore, but at the user login I here the ubuntu marimba sound. I also seem to have lost certain programs in my gnome menu, all the programs that needed administrative rights have disappearded. 

I tried running KDE and it's the same deal, no sound, no windows drives.

Any suggestions?

---

### Post by ayoli on 2007-05-04
you may post some logs to help like:
```
/var/log/syslog
~/.xsession-errors
```
especially parts concerning these strange reboots

---

### Post by forchessonly on 2007-05-04
bgates@bgates-desktop:~$ /var/log/syslog
bash: /var/log/syslog: Permission denied
bgates@bgates-desktop:~$ ~/.xsession-errors
bash: /home/bgates/.xsession-errors: Permission denied
bgates@bgates-desktop:~$ sudo /var/log/syslog
Password:
bgates is not in the sudoers file.  This incident will be reported.
bgates@bgates-desktop:~$ ~/.xsession-errors
bash: /home/bgates/.xsession-errors: Permission denied
bgates@bgates-desktop:~$ sudo ~/.xsession-errors
bgates is not in the sudoers file.  This incident will be reported.

It seems I've lost super user privaledes....

---

### Post by Ptero-4 on 2007-05-04
That shutoff must have f*cked some sensitive files (USB drives tend to get f*cked badly by sudden shutoffs since they´re very sensitive to power anomalies).

---

### Post by forchessonly on 2007-05-05
I think this might be my cue just to reinstall. It shouldn't take too long to set it all up again, considering I only installed it like a month ago. This time I'm gonna remove openSuse and install ubuntu to my internal drive and just use my ext3 partition on my external usb as storage for non system files. But crap, that means I'm gonna have to replay my way through neverball again. Beating that game took some crazy determination.

Unless someone performs a miracle and tells me how to fix this...

---


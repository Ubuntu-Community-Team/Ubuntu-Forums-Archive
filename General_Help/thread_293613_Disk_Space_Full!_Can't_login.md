---
title: "Disk Space Full?! Can't login"
date: 2006-11-05
forum: General Help
---

### Post by hemple on 2006-11-05
I am running  Dapper Drake Ubuntu on my laptop and most problems I face are minute.But, I am attempting to log in and an error message is displayed.

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem. 

(when the VIEW DETAILS button is checked)

/etc/gdm/PreSession?Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" " -l ":0" "dan"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp : private socket dir: No space left on device   "

and to confirm the lack of disk space, i ran df -h and in fact there is nothing.


i started to upload a lot of videos from my camcorder, and i believe my friend set it up so the videos are saved right to the root. i was reading somewhere on here that that is not good and may cause this problem.  my idea is the videos filled up the temporary files. but i have no idea what im talking about.

yesterday before this happened i had close to 28 gB and now i have nothing?! impossible i would like to think.

anybody know what the problem might be. and any suggestions on another way to get my video onto my laptop if that is the cause of this?

thanks. -dannnn

---

### Post by an.echte.trilingue on 2006-11-05
Yup, your disk is full.

Get a liveCD (i prefer [slax]("http://http://www.slax.org/"), much faster than the ubuntu CD or knoppix) and delete some stuff, or you can do it from the command line since you seem to be able to log into failsafe.  In the future, you can partition your HD so that this does not happen by making a partition of, say, 10GB, and mounting it at, say, /media/movies/.  Then, if you lose track of how much space you are using, all that will happen is that the specific app that is writing to that file will return an error when the partition is full.  Alternatively, you can just keep better track of you much disk space you are using.

By the way, if you ever fill up your root directory "/", your system will (AFAIK) crash and be unbootable until you boot with a liveCD or bootable floppy and make some space.  So, probably your videos are being saved to your home directory, which in turn is probably on its own partition, although i think that this error can happen if you have /var on its own partition and you fill that partition up.

If you post the output from df we can help you figure out exactly what to delete.

Take care, mat

---

### Post by bettlebrox on 2006-11-05
Go to the console (CTRL-ALT-F1) and login and free up some space. CTRL-ALT-F7 will bring you back to the GUI login.

---


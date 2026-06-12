---
title: "[SOLVED] Your session only lasted less than 10 seconds..."
date: 2007-08-09
forum: General Help
---

### Post by c_cammann on 2007-08-09
Hi I have a problem that I hope someone can help me with.

I was installing language support for Japanese on my computer (Toshiba Satelite M55-S3512 running Ubuntu Feisty Fawn) and it terminated without finishing the install and when I rebooted it didn't enter gnome. It gives me the error message:

Your session only lasted less than 10 seconds... that I see alot here. One explination that I see is that my disk is actually full. My .xsession-error reads:

/etc/gdw/PreSession/Default: Registering your session with wtmp and utmp /etc/gdm/PreSession/Default: running: /usr/X11R6.bin.sessreg -a -w .var/log/wtmp -u /var/run/utmp -x "/var/lib/gbm/:0.Xservers" -h "" -l ":0" "alden" /etc/gdm/Xsession: Begining session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc.X11.xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: NO space left on device
~
~
~


So if my device is full, how much of what do I need to delete? Do you think my disk is actually full? given this message and xsession-error printout?

Any and all help welcomed (please with responses remember that I am fairly new so I need complete instructions. Thanks!)

-Alden

---

### Post by Arisna on 2007-08-09
The quickest way to find out whether you are in fact out of disk space is as follows:

1.) Boot Ubuntu.
2.) Wait until you've received the error message you described.
3.) Press Ctrl+Alt+F1.
4.) Log into your user account.  Note that your password will not be echoed on screen.
5.) Enter the command "df -h" (without quotes)

The system will then output disk usage information, one filesystem per line.  You're looking for any filesystem that has around 100% usage.

---

### Post by c_cammann on 2007-08-09
Okay thanks. 

Yes my / folder is full. But there is plenty of room in home. is there a way to adjust the partitions? or at least what could I erase in order to boot up so that I can back up and reinstall?

- Alden

---

### Post by aysiu on 2007-08-09
```
sudo apt-get clean
``` will free up some space.

---

### Post by c_cammann on 2007-08-09
Worked Great Thanks!!
-Alden

---


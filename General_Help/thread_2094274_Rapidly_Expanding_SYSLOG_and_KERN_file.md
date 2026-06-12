---
title: "Rapidly Expanding SYSLOG and KERN file"
date: 2012-12-13
forum: General Help
---

### Post by cyberphrog on 2012-12-13
I recently replaced my desktop hard drive (500G) and upgraded to 12.04 in the process.  All in all, about 1/3 of the HD was filled after installing 12.04 and restoring my files.  It's been working great until a few days ago, when I noticed slower performance and desktop messages indicating that I had very little space left on the HD (<1G).  I did some digging into the file directory this morning to find that my syslog and kern files were HUGE (syslog was ~285G, kern was ~100G), and growing.  I decided to reboot and now can't get onto the admin login at all, it appears that these two files have been quietly growing and now have completely bogged everything.  Any thoughts on what I can do, short of wiping the drive and starting over??

---

### Post by dino99 on 2012-12-13
if you are talking about the log files, then simply delete them, and install logrotate (it should be already installed on a genuine installation)

or do a fresh install to get rid of the oldish/borked settings files/folders.

---

### Post by SeijiSensei on 2012-12-13
If your system is generating logs of this size, you have a problem that needs investigating.  I suggest rebooting into recovery mode, so the logs won't continue to fill, then using "tail -n1000 /var/log/syslog" to see the last 1,000 lines of that file.

---

### Post by cyberphrog on 2012-12-13
Thanks, will give it a try tonight...

---

### Post by cyberphrog on 2012-12-14
The drive is fully consumed and Ubuntu will not boot.  I was able to recover/backup files by booting on the install disk.  Going to start back at square-one and do a fresh install this weekend with a new install disk...

---

### Post by Ms. Daisy on 2012-12-14
You couldn't boot it in recovery mode either?

---

### Post by cyberphrog on 2012-12-18
Couldn't boot in recovery mode. Fresh install appears to be working fine, so far.

---


---
title: "BackupPC Web Interface Missing"
date: 2007-10-24
forum: General Help
---

### Post by bgearig on 2007-10-24
Basically, when running 'sudo apt-get install backuppc' on a Gutsy Gibbon LAMP server, there is no web interface to login to for BackupPC!  I found the problem to be that there was no configuration added to Apache2 to point to BackupPC's CGI-Bin.  There is a file in the '/etc/backuppc' directory named 'apache.conf' and in it are the lines that are to be used for the web interface.  If I manually copy them into Apache2's configuration file, then the web interface works.

My problem is, anytime I have used the apt-get method of installing BackupPC, the web interface was automatically taken care of.  Is this supposed to be the same in Gutsy Gibbon?  Or was everything I did the correct way to enable web interface?

---

### Post by bgearig on 2007-10-25
BUMP

I really need to know why it won't automatically configure the apache config file to display the backuppc web interface.  I am pretty sure it used to do so...  So I am wondering if it has to do with my Ubuntu installation...

*EDIT*  I went ahead and just used the code as follows and took note of it for future reference so I don't have to type everything out:

sudo chmod 777 /etc/apache2/apache2.conf
sudo cat /etc/backuppc/apache.conf >> /etc/apache2/apache2.conf
sudo chmod 644 /etc/apache2/apache2.conf
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

VOILA!

*/EDIT*

---

### Post by benblank04 on 2007-10-31
seems I am not the only one with this issue, I will have to try what you did tomorrow! Thanks!

---

### Post by uhu_maotouying on 2007-11-07
Thanks a million bgearig :
This works for me with Ubuntu 7.10 x64 !
uhu

---


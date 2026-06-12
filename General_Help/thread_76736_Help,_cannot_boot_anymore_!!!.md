---
title: "Help, cannot boot anymore !!!"
date: 2005-10-15
forum: General Help
---

### Post by eviau on 2005-10-15
Hi:

After having installed a few things from Synaptic, I cannot boot anymore under any user name (There are 3 on my computer). I get the message : "GDM cannot write in your authorisation file. You could be short in hard disk space, or your personnal file cannot be opened in write mode, etc." (This may not be the exact english text though, since I translated it from french). My hard disk is only half full.

I can enter the Linux "Safe Mode" at boot by typing ESC, but since I am still a human being ;) I do not know how to use the command line mode... Booting in safe mode as root user, I can however see files of all the users.

Could you help? Since I switched from Windows to Ubuntu, I now cannot access anymore to my files ! :mad: 

Thanks,

---

### Post by Lord Illidan on 2005-10-15
Mind telling us what you installed? "A few things" just doesn't cut it!

---

### Post by eviau on 2005-10-15
[QUOTE=Lord Illidan]Mind telling us what you installed? "A few things" just doesn't cut it![/QUOTE]

I installed the Apache-ssl, PHP4, plus support from various options, the last one being Mysql for PHP4. I was trying to use the egroupware suite.

---

### Post by metoo on 2005-10-15
Dropped to the console?
'df -h' gives you an overview of your drive utilization.

'sudo apt-get update' fetches new package lists.
'sudo apt-get upgrade' updates all of your installed packages.
'sudo apt-get dist-upgrade' gives you, well, a dist-upgrade.
If you think, you have a broken package, try:
'sudo apt-get install --reinstall package-name'

See at the end of the status you get after an apt-get command: there should be listed if you have any not configured packages. In that case try:
'sudo apt-get -f install'

Unfortunately, you have to be on-line to fetch new packages.
If you can get on-line, having a router for instance, you may want to delete everything in /var/cache/apt/archives to force a re-download of the packages you re-install. May be there was one just corrupted during the last download.

P.S. I'm not sure, whether you actually need sudo in recovery mode.

---


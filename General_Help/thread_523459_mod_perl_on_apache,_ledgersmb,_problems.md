---
title: "mod_perl on apache, ledgersmb, problems"
date: 2007-08-11
forum: General Help
---

### Post by Idfy on 2007-08-11
I have recently had the need to use ledgersmb for accounting stuff. However, I seem to have problems. I used this install guide: [http://ubuntuforums.org/showthread.php?p=3109659](http://ubuntuforums.org/showthread.php?p=3109659) and everything went smoothly. Once I restarted apache I opened up a browser and headed towards to [http://localhost/ledgersmb/](http://localhost/ledgersmb/) and I get prompted to download the login.pl script. 

I knew this wasn't right. So I thought maybe it was because mod_perl wasn't installed. So I looked in the repositories and got the libapache2-mod-perl2 package and installed it. Once restarting and reloading the apache server I headed to locahost again and the problem persist. The only change was now the server identified itself as Apache/2.2.3 (Ubuntu) mod_perl/2.0.2 Perl/v5.8.8 Server at localhost Port 80

I am stumped. Any ideas?

---


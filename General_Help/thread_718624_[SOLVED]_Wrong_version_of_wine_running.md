---
title: "[SOLVED] Wrong version of wine running"
date: 2008-03-08
forum: General Help
---

### Post by Redenbacher on 2008-03-08
I just installed wine 0.9.57 from gutsy repositories, and just realized that when I run wine --version, it returns that I am running wine 0.9.50, which means that it probably hasn't changed for the past 7 updates... How do I remove the old versions and ensure that I am running latest? Thanks in advance for the help :)

If memory serves, 0.9.50 was the last one I installed from source, but I've no idea where I installed it to!

---

### Post by insineratehymn on 2008-03-08
Wow... Ubuntu's on that bleeding edge, 0.9.57 just came out yesterday!

Anyway, just did the upgrade myself from 0.9.56 and wine --version says:

wine-0.9.57

apt-cache policy wine says:

wine:
  Installed: 0.9.57~winehq0~ubuntu~7.10-1
  Candidate: 0.9.57~winehq0~ubuntu~7.10-1
  Version table:
 *** 0.9.57~winehq0~ubuntu~7.10-1 0
        500 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
        100 /var/lib/dpkg/status
     0.9.56-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages

Sooooo..... I dunno.
Have you tried getting the 0.9.57 deb directly from wine?

[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.57~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.57~winehq0~ubuntu~7.10-1_i386.deb)

I believe that will take you straight to it.
Let me know what wine --version and apt-cache policy wine say.

---

### Post by ahaslam on 2008-03-08
Have you tried *wineprefixcreate*?

---

### Post by Redenbacher on 2008-03-08
Hmmm no I haven't tried any of those things, but I will.

Just to clarify however, I don't think the problem is that wine is not installed properly, I just think it's installed twice, and running "wine" runs the old install instead of the new one. Is there any way to locate and destroy the old installation?

I tried grep wine-0.9.50, but I don't think that is the right command! I also tried using the search feature in a file to find wine-0.9.50, but it turns up nothing.

---

### Post by mc4man on 2008-03-08
When you compiled wine you would have had a folder wine-0.9.50 (usually either on desktop or in home) If you haven't deleted it and used make install then in terminal cd to that folder and run sudo make uninstall. Note - just noticed you searched for it - try searching wine instead (file system) and look for folders.
The default install for your compile would have been /usr/local  (vs. debs which install to /usr). You'll probably find your .50 install in /usr/local/bin

---

### Post by Redenbacher on 2008-03-08
> The default install for your compile would have been /usr/local (vs. debs which install to /usr). You'll probably find your .50 install in /usr/local/bin

You were absolutely right! That's where it was. Deleted all the wine files, opened up a terminal and punched in winecfg, checked the version and 9.57 is running now. Thanks!

---


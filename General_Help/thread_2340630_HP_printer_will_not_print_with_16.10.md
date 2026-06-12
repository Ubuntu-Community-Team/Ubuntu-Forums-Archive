---
title: "HP printer will not print with 16.10"
date: 2016-10-20
forum: General Help
---

### Post by aridus on 2016-10-20
Upon upgrade from 16.04 to 16.10 I am no longer able to print or scan (either with a USB connection or by wireless) on my HP Laserjet MFP M125 NW. I can install/reinstall the printer but every print job is reported as 'stopped' in the print queue. The printer was fine with 16.04. Has anybody else run into this problem and/or have a solution?

Many thanks!

---

### Post by Hewjr100 on 2016-10-20
Wish I could help, but my hp printer works fine.  One thing though I never upgrade from one version to another.  I just do a fresh install.

Henry

---

### Post by aridus on 2016-10-20
Many thanks. I suppose that is an option but I have so many things installed and 16.10 otherwise runs fine that I am reluctant to do a fresh install. I have tried purging and reinstalling hplip but that has not helped.

---

### Post by fyfe54 on 2016-10-20
I have the same "stopped" issue  (LaserJet Pro MFP M127fn) and have not come across a solution.  Yet.  

The installer dropdown only goes up to 16.04. so we may need those nice folks at HP to provide support for 16.10.

---

### Post by aridus on 2016-10-21
I have tried to install hplip v. 3.16.9 from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) (this is a later version than that available with 16.10) but it fails at the last stage. I continue to search as I need to print a 50 page document urgently but perhaps fyfe54 is correct, and we have to wait for HP.

---

### Post by joefiallo2 on 2016-10-26
I had the same problem.  
I removed and reinstalled hplip. During the installation I observed the message /etc/hp/hplip.conf missing ....
So I copied hplip.conf from another computer (running Ubuntu 16.04)
Then i could run "hp-setup" whithout error.
Now I can print and scan on my network printer MFP M125nw 

Joe Fiallo

---

### Post by fyfe54 on 2016-10-26
THe nice folks at HP have updated HPLIP and it now installs for 16.10.  No errors and printing is perfect.

---

### Post by aridus on 2016-10-27
They have indeed!

---

### Post by lfm166 on 2016-10-29
i have hp laserJet 1020 work in ubuntu 16.10 :)
you have to download the driver [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and select ubuntu 16.10 and run hplip-3.16.10.run

---


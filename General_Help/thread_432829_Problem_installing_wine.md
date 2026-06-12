---
title: "Problem installing wine"
date: 2007-05-04
forum: General Help
---

### Post by LuckN1ne on 2007-05-04
ok im falling this guide [[http://ubuntuforums.org/showthread.php?t=149585&highlight=wine]](http://ubuntuforums.org/showthread.php?t=149585&highlight=wine]) and when i get this problem


> james@james-desktop:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgtk1.2: Depends: libgtk1.2-common (>= 1.2.10-18) but it is not going to be installed
             Depends: libglib1.2 (>= 1.2.0) but it is not going to be installed
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-11-1ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
james@james-desktop:~$ apt-get -f installE: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
james@james-desktop:~$ 


---

### Post by phidia on 2007-05-04
Sometimes that last error "Unable to lock.." can be about another package manager being open?
I might be wrong though. If you're trying to install wine and it's not working from the ubuntu repos you might want to check the info at wine's website. [http://www.winehq.com/](http://www.winehq.com/)

---


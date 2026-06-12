---
title: "adept manager won't let me install"
date: 2008-01-17
forum: General Help
---

### Post by cpmpal on 2008-01-17
Having  trouble install anything from adept (in Kubuntu).

either it cannot "lock" the folder

or the cannot commit changes error 

or a dpkg error

i have checked ran update dpkg -f and all the other adept fixes i have seen through the forums and i am stuck, ...really stuck

help would be awesome:)

---

### Post by sumguy231 on 2008-01-17
Look for any running processes that might be using the package management system, such as apt, aptitude, adept, or dpkg. If you don't see anything obvious, try rebooting to see if it frees it up. Also, what error output does apt-get -f install give?

---

### Post by MFinkel on 2008-01-17
Hi sumguy231, I to am having an adept issue also. Most of my downloads say installed and no change. I also can not download boinc or firefox. I especially need firefox. I ran an auto clean I believe it is called a few times to get some errors resolved which it finally did. Still no joy. I ran the code in this thread and this is the result:
 apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
I used the cd to download kubuntu 7.10 and have not been able to use the adept since install.
I know this is an old post but I hope you are still around and can help me, Thanks, M

---

### Post by sumguy231 on 2008-01-17
> **MFinkel said:**
> Hi sumguy231, I to am having an adept issue also. Most of my downloads say installed and no change. I also can not download boinc or firefox. I especially need firefox. I ran an auto clean I believe it is called a few times to get some errors resolved which it finally did. Still no joy.
Could you give error messages/output for those too?

> I ran the code in this thread and this is the result:
 apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Easy fix, you just need to run it with admin privileges. Do this instead, and enter your password:
```
sudo apt-get -f install
```
Any time you use the package manager you will need to use sudo because normal users are, for security reasons, not allowed to install software.

> I know this is an old post but I hope you are still around and can help me, Thanks, M
It's only been 40 Minutes. :)

---

### Post by MFinkel on 2008-01-17
Sorry, 1st off, I looked at your join date. oooops.
I ran the new code you requested and here is the result:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail           able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc           ess using it?
Thanks, M

---

### Post by SOULRiDER on 2008-01-17
Try
```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

---

### Post by sumguy231 on 2008-01-17
Edit: beaten like a dead horse.

---


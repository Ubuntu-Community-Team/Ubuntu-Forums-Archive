---
title: "Terminal/Bash not working"
date: 2013-08-13
forum: General Help
---

### Post by lordziconoah on 2013-08-13
cant use my terminal to update or install programs. here is the feedback i get   root@john:/home/john# apt-get install update E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?    please helpme out

---

### Post by lordziconoah on 2013-08-13
root@neonard:/home/neonard# apt-get install update E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by lordziconoah on 2013-08-13
thats the feed back i get when trying to use terminal for update or installing any program

---

### Post by zombifier25 on 2013-08-13
Is there another package-related program that's opening (such as Ubuntu Software Center, Synaptic, Update Manager)? If so, close all of them and try again.

If not, then usually a reboot of the system should fix it. If it still hasn't been fixed, then post again.

---

### Post by lordziconoah on 2013-08-13
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

its still the same

---

### Post by cortman on 2013-08-13
I wrote a [blog post detailing how to fix this]("http://cortman.wordpress.com/2012/02/24/unable-to-obtain-lock-for-software-installation/").

---


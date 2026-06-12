---
title: "Overwritten PATH, can't log in."
date: 2016-07-30
forum: General Help
---

### Post by sirbearington on 2016-07-30
I mistakenly over wrote the PATH variable and can no longer log in to my user. I tried entering tty and exporting a new PATH but am not able to get sudo su to work due to the broken PATH variable. 
I have found some posts similar to this but they where not my solution. Mainly because they didnt mention the users having sudo issues.
Any ideas?

---

### Post by steeldriver on 2016-07-30
Hello and welcome to the forums

Did you try simply giving the full path to sudo? for example, if you overwrote your path in /etc/environment, then you should be able to correct it using

```

/usr/bin/sudo nano /etc/environment

```

---

### Post by sirbearington on 2016-07-30
Thank you,
That helped me solve it.
To elaborate.
After adding usr/bin/sodu to PATH and running sudo the Path would reset to what it was before but resetting it again after gaining root access solved the issue.

---


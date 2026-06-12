---
title: "apt-get help"
date: 2006-11-16
forum: General Help
---

### Post by M!K3_$ on 2006-11-16
while trying to install some aps and plugins using automatix
my apt-get got screewy
i got to the part of the sun java bit were it asks me to push ok
but i couldnt figure out how to do that (tryd to press enter)
so i just closed it and automatix just carried on

now i tryd to fix it
and it says the apt-get is busy ????
so **is ther a way to shut down the apt-get** so that i can cancel the installation of the sun java plugin :S

here is a pic of the message i get

thankx mike

---

### Post by adwait on 2006-11-16
Try renaming the lock file, /var/lib/dpkg/lock suing
```
sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock.backup
```

---

### Post by feest on 2006-11-16
ubuntu can only run one intallation program at a time, so if you are running synaptic, apt won't work. it's the same for automatix so if you didn't shut it down correctly it might still think its runnning. maybe start automatix again and let it install something small and and close it when its done. does it work now?

---

### Post by M!K3_$ on 2006-11-16
fixd it

thankx guys
mike

---

### Post by Abdo375 on 2007-02-02
I'm having the same problem when trying to install vm-player can someone plz help me.
thanks.

---

### Post by ~LoKe on 2007-02-02
Close Synaptic.

---


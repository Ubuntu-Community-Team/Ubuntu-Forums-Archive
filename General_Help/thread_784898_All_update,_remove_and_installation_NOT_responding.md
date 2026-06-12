---
title: "All update, remove and installation NOT responding"
date: 2008-05-06
forum: General Help
---

### Post by daveloh on 2008-05-06
i Juz download Ubuntu 8.04 LTS n back up my Ubuntu 7 and fresh install Ubuntu 8.04 desktop...

well....Ubuntu 7 was serve me very well...juz that may be the hardware driver make me think too much sometime, but i still luv it.

the problem is........the system update prompt....when i click on it n try to update....the updater halt....

i restart my machine...

then i wanna to install OpenOffice database, once i click install.....the program halt...

cannot shut down the program....i restart again...

after restart...i open firefox.....flash movie prompt me for install plugin...i click to install....same thing happen...

can this thing being fixed??? or i need to go back to Ubuntu 7 or my Ubuntu 8 beta version???

---

### Post by Tyke91 on 2008-05-06
8.04 is no longer in beta.

try doing
```
sudo apt-get update
```and please paste the output here

---

### Post by daveloh on 2008-05-06
it give me this output......
> sudo: unable to resolve host daveloh-mis

---

### Post by debeyt on 2008-05-06
Since upgrading to 8.04 LTS, I am having exactly the same problem. Also, there are times the system will start without asking for a username/password. 

I have also tried 'sudo apt-get update' and get the message sudo: 'unable to resolve host tom-linux'

Any ideas out there?

---

### Post by daveloh on 2008-05-07
nobody can help???

---

### Post by kesman on 2008-05-07
[http://ubuntuforums.org/showthread.php?t=782738](http://ubuntuforums.org/showthread.php?t=782738)
From this thread, check these two files:
```

/etc/hosts
/etc/hostnames

```
and if there's something after your hostname in /etc/hosts, boot to recovery mode and edit the file. Remember to take a backup first.

---

### Post by daveloh on 2008-05-12
well.....this is working...
thks for help~~~

---


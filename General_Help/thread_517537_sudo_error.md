---
title: "sudo error"
date: 2007-08-04
forum: General Help
---

### Post by hansteam on 2007-08-04
Hey guys,

I'm getting a strange error when I type in sudo commands. I'm currently trying to get my speakers working on a Toshiba Satellite P105. I found a thread that gives some code specifically for my model, but when I type in the following command

```
 sudo apt-get install iasl

```

I get the following error message(s)

```
sudo: /etc/sudoers is owned by uid 1000, should be 0
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

```

I assume that this is a result of some bad advice that I received when I was trying to resolve the same problem with my speakers (go figure, it didn't work...). I can't remember the code that was involved in that but I think it was something to the extent of:

```
sudo chown -R <username> /$
sudo chmod -R 664 /$
```

Thanks in advance, I'm sure someone somewhere knows what to do :D

C

---

### Post by dreadlord_chris on 2007-08-04
hmmmm.....
boot into recovery mode
```

chown root:root /etc/sudoers
shutdown -r now

```
*should* fix your sudo problems

---

### Post by hansteam on 2007-08-04
Unfortunately, that solution did not work. It seems that I actually had no root:root user on my system. Shortly after discovering that, I restarted my system and discovered that there were no users on my system. I had to reinstall ubuntu. Luckily, I have been doing this every day for the past 4 while I've been switching from Vista. Your solution definitely would have worked had I not lost my root user and I appreciate your help

regards,
C

---


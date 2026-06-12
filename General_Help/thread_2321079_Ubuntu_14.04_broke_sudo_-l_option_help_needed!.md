---
title: "Ubuntu 14.04 broke sudo -l option help needed!"
date: 2016-04-20
forum: General Help
---

### Post by erwinzero on 2016-04-20
Hi,

Today I shrink my Ubuntu main disk form 20GB to 10GB. No problem encounter, ubuntu is working. But now I wanted to install a program with sudo rights. Normaly I do sudo (commando) but this time I needed to do alot of commando's. So i thought let use sudo -l. But here came the problem

If I use sudo then a commando no problem
If I use sudo -l ill get this:

Erwin@ubuntu:~$ sudo -l
Matching Defaults entries for erwin on ubuntu:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin


User erwin may run the following commands on ubuntu:
    (ALL : ALL) ALL

Dont know how to fix this.

I have tryd to reinstall Sudo without any succes.

---

### Post by mcduck on 2016-04-20
Looks you ran "sudo -l" (with a lower-case L, which lists what commands user is allowed to run through sudo), while I suppose you intended to run "sudo -i" (which starts root login shell)?

---

### Post by erwinzero on 2016-04-20
Thanks :) that was the problem!. Dont know why i used L instead of i :S problem solved :)

---

### Post by ajgreeny on 2016-04-20
Please mark as SOLVED from the Thread Tools menu at the top.

---

### Post by grahammechanical on 2016-04-20
Problem solved. May be, But there could be a better way.

Once we run one command using sudo & after entering our password we can enter other commands without the need to enter the password a second or third time. We continue as administrator for a certain period of time.

Then we can run more than one command at the same time. For example:

```
sudo apt-get update && sudo apt-get upgrade
```

will run both commands and we only need to enter our password once.

Regards

---


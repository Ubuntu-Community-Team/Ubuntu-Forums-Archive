---
title: "ubuntu 12.10 software updater serious problem"
date: 2013-07-06
forum: General Help
---

### Post by babakflame on 2013-07-06
Dear Buddies
Hi

Whenever I ran sudo apt-get update on terminal, I confront this error:

```
babak@babak-System:~$ sudo apt-get update
[sudo] password for babak: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

  Would some expert guy help me?  My ubuntu is 12.10 (Quantal)
  Regards

---

### Post by Impavidus on 2013-07-06
Are you sure no other package managers are running? Software centre, synaptic, ... You can only run one at a time.

---

### Post by babakflame on 2013-07-06
Hi
I am just running a C++ code on ubuntu and no other program including package manager is running.

Bobi

---

### Post by babakflame on 2013-07-10
Hey Guys
  What should i do?

---

### Post by chenzero on 2013-07-10
please try:
reboot the computer, and run that command again.
if still problem, that sounds like is a 12.10 bug.

---

### Post by chenzero on 2013-07-10
another way is, run following command to find which process is opening that file

$ sudo lsof | grep /var/lib/dpkg/lock

Note that this command takes a while to enumerate files, that might include socket files

---


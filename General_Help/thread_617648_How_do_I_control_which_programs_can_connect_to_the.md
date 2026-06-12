---
title: "How do I control which programs can connect to the internet?"
date: 2007-11-19
forum: General Help
---

### Post by startling on 2007-11-19
On Windows, programs such as Zone Alarm can be used to control which programs are allowed to access the internet. How can I achieve this with Ubuntu?

---

### Post by rye_ on 2007-11-19
sounds to me that your about to get a shell script tutorial :)

---

### Post by Shazaam on 2007-11-19
Here is the main security page...

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Iptables is your FIREWALL built into the kernel. Go here to learn about it...

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

There are several GUI front ends that make it easier to configure iptables. Here is one...
FireStarter...

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by startling on 2007-11-19
> **Shazaam said:**
> 
There are several GUI front ends that make it easier to configure iptables. Here is one...
FireStarter...


Thanks for your help, Shazaam. 
On the page that your second link directed me to it said: 
*Personal note: Unfortunately, it [Firestarter] does not have the option to block (or ask the user about) connections of specific applications/programs... Thus, my understanding is that once you enable port 80 (i.e. for web access), any program that uses port 80 can connect to any server and do anything it pleases...*

 I must admit that all that stuff about iptables looks daunting for me, but I will have a read and see if I can understand any of it.

---

### Post by Shazaam on 2007-11-19
Hmm. I'm not sure (it's been a long time since I used it) but GuardDog (for KDE but you can install it on Gnome) might be able to help. It's in the repos and it's another GUI for iptables.

[http://www.simonzone.com/software/guarddog/](http://www.simonzone.com/software/guarddog/)

Personally I think it's (GuardDog)  more confusing than FireStarter for a new user but It can be sussed out. Read and follow the instructions and you will be fine.
One thing about configuring iptables manually is you get to learn and understand the guts of it. Unfortunately I am still a little bit brainwashed into relying on GUI's but I am slowly learning to use the cli (command line interface). If I had started out with DOS instead of Win98 it wouldn't be so bad. :)

---

### Post by bodhi.zazen on 2007-11-19
I suggest you look at Apparmor :

[Firewall your applications with AppArmor](http://www.linux.com/articles/58789)

[Protect your applications with AppArmor](http://www.linux.com/articles/114162)

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)   <- Ubuntu wiki

---

### Post by Shazaam on 2007-11-19
Apparmor a no-go for Dapper?

---

### Post by bodhi.zazen on 2007-11-19
> **Shazaam said:**
> Apparmor a no-go for Dapper?

That is a good question. I wonder if you could compile from source ?

---

### Post by startling on 2007-11-20
> **bodhi.zazen said:**
> I suggest you look at Apparmor :

[Firewall your applications with AppArmor](http://www.linux.com/articles/58789)

[Protect your applications with AppArmor](http://www.linux.com/articles/114162)

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)   <- Ubuntu wiki


Thank you bodhi.zazen. That's very helpful.

---


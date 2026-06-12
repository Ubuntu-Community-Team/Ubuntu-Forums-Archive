---
title: "ssh: connect to host port 22: Connection refused"
date: 2014-04-29
forum: General Help
---

### Post by devi2 on 2014-04-29
Hi all,

(*excuse me for my bad english*)

Since I did a "reboot now", I can't reconnect ??

I am a beginner and I need some help please.

Regards,
Devi




devi@devi-ThinkPad-T60:~$ ssh root@guess
root@guess's password: 
Welcome to Ubuntu 13.10 (GNU/Linux 3.11.0-18-generic x86_64)


 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


  System information as of Tue Apr 29 10:23:20 NCT 2014


  System load:  0.08               Processes:           100
  Usage of /:   62.3% of 51.06GB   Users logged in:     1
  Memory usage: 9%                 IP address for eth0: 172.16.30.101
  Swap usage:   2%


  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)


10 packages can be updated.
10 updates are security updates.


New release '14.04' available.
Run 'do-release-upgrade' to upgrade to it.


*** Le système doit être redémarré ***
Last login: Mon Apr 28 08:33:47 2014 from 172.16.23.211
root@guess:~# reboot now


Message de diffusion de root@guess
    (/dev/pts/0) à 7:53...


L'ordinateur va s'arrêter pour maintenance MAINTENANT !
root@guess:~# Connection to guess closed by remote host.
Connection to guess closed.
devi@devi-ThinkPad-T60:~$ 


devi@devi-ThinkPad-T60:~$ ssh root@guess
ssh: connect to host guess port 22: Connection refused

---

### Post by ian-weisser on 2014-04-29
I would first check the router to see if guess was issued a different IP address.
Did you perhaps disable root logins on guess' ssh server? Many online instructions for setting up SSH servers include that step.

---


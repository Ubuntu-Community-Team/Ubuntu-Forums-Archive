---
title: "Restrict Login Access Times for son."
date: 2013-08-01
forum: General Help
---

### Post by derek_mitchell2 on 2013-08-01
I'm setting up my son's computer with Ubuntu 12.04. He has a tendency to install a lot of stupid stuff on the computer with windows. So i've went this route. I need to control the times that he is online. 

At the end of /etc/security/time.conf I placed this line:
*;*;tj;SuMoTuWeTh0900-2145|FrSa0900-2300

According to what I've read this should only allow him to login during the time frames listed there. 

I updated my etc/pam.d/login to include:

account    required   pam_time.so



No matter how I tinker around with these settings he is still able to login. Any help on where to go. Nanny doesn't want to work for 12.04

---

### Post by GwL3eNC on 2013-08-01
Hi derek_mitchell2,

there is an older post about some applications parents can use.
[http://askubuntu.com/questions/68918/how-do-i-restrict-my-kids-computing-time](http://askubuntu.com/questions/68918/how-do-i-restrict-my-kids-computing-time)

---

### Post by Lars Noodén on 2013-08-02
The magazine Linux Format issue 172 from July had a detailed article on how to set that up.  The article is "Child's Play: Setting Limits" and starts on page 90.   Check your library for paper copies.

---


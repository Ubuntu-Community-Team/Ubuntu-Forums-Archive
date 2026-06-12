---
title: "How do I reset host name"
date: 2004-11-12
forum: General Help
---

### Post by Tomy on 2004-11-12
I now have ubuntu installed on two computers and I just accepted the default ubuntu host name.
 
 How do I change the host name?
 
 Tomy

---

### Post by ubuntu_demon on 2004-11-12
sudo pico /etc/hostname

You might want to reconfigure postifx too (sudo dpkg-reconfigure postfix)

---

### Post by Tomy on 2004-11-12
Thanks,
   that was easy
   
   Tomy
  
  ps  oops, I got an error on reboot and had to change /etc/hosts also.

---


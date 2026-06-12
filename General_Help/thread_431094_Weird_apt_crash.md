---
title: "Weird apt crash"
date: 2007-05-02
forum: General Help
---

### Post by Hide on 2007-05-02
Hi all

I'm having a weird apt problem. After a PC restart, systeam fell insto framebuffer, and there was an error similiar to this one:
[b]couldn't find package apt, intall it by 
apt-get install apt[/b].

I used LiveCD to download apt, copied it, and install it to my HDD, but it didn't work :(

thx in advance :)

---

### Post by Hide on 2007-05-24
Ok, this is starting to irritate me! I cant install any other distro to my second HDD without Ubuntu crashing! Help, anyone?

---

### Post by Hide on 2007-05-24
It was so god damn easy! Erase the UUID code and uncommemt /dev/hdX line in /etc/fstab ;). Works like charm ;).

---


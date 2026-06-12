---
title: "Graphics issue"
date: 2016-12-23
forum: General Help
---

### Post by ex-para on 2016-12-23
I have trouble with 16.04 as when I go to search computer it just flashes all the time so I tried this

Log into your account in the TTY. 
1. Run sudo apt-get purge nvidia-* 
2. Run sudo add-apt-repository ppa:graphics-drivers/ppa and then sudo apt-get update. 
3. Run sudo apt-get install nvidia-364. 
4. Reboot and your graphics issue should be fixed. 
All went well untill the last command where  (nvidia-364.) could not be found.
What should I do.

---


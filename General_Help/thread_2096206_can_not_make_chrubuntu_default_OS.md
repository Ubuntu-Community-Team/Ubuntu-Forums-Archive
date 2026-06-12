---
title: "can not make chrubuntu default OS"
date: 2012-12-19
forum: General Help
---

### Post by bodagala on 2012-12-19
Hi everyone
I am a new member

I have installed Chrubuntu on my Acer C7 in developer mode. After rebooting it went back to chrome.

I entered sudo cgpt add -i 6 -P 5 -S 1 /dev/sda in developer mode on chrome OS. When I entered this command it did not give me any response. also did not ask for a pass word. I am supposed to enter password  user  .

I rebooted again. I am still getting chrome.

Please anyone help me ?

Siva):P

---

### Post by durbe86 on 2013-01-10
> **bodagala said:**
> Hi everyone
I am a new member

I have installed Chrubuntu on my Acer C7 in developer mode. After rebooting it went back to chrome.

I entered sudo cgpt add -i 6 -P 5 -S 1 /dev/sda in developer mode on chrome OS. When I entered this command it did not give me any response. also did not ask for a pass word. I am supposed to enter password  user  .

I rebooted again. I am still getting chrome.

Please anyone help me ?

Siva):P

I am also experiencing the same problem. During installation, I did have to restart the chrbuntu installation again in the chrome os terminal and I wonder if it created a superfluous partition or chrbuntu image? Some help here would be greatly appreciated!

---

### Post by Luca_Santarella on 2013-08-30
I solved the problem. 
After logging in as chronos in Chrome OS, type:

sudo cgpt add /dev/sda -i 6  -P 5 -S 1


That should fix.

---

### Post by oldrocker99 on 2013-09-05
Do bear in mind that in using the cgpt command, case and spacing are **critical**.

---

### Post by richard24 on 2013-10-01
Some installed ChrUbuntu on Samsung Chromebook?

---


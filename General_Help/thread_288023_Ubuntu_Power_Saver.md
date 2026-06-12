---
title: "Ubuntu Power Saver"
date: 2006-10-29
forum: General Help
---

### Post by Sethro on 2006-10-29
Hi I just installed Ubuntu 6.10 and I really want to squeeze out as much battery power as I can, so right now my CPU scaling frequency is set as Ondemand. How do I set it to Powersave I tried the CPU Scaling feature but I cant access any govenors. 


Thanks,
My set up :

user name : sethro
CPU : Hyper Threading : CPU0, CPU1
3.06 GHz


Thanks for your help

---

### Post by Sethro on 2006-10-29
Yeah and when I try to set it in Ubuntu 6.10 I cant access the govenors

---

### Post by bonsiware on 2006-10-29
Try:
```
sudo chmod +s /usr/bin/cpufreq-selector
```

---

### Post by Sethro on 2006-10-29
Thank YOU!

U R GOD! lol

---

### Post by transatlant1c on 2007-08-16
What does this do? I've been trying to save as much battery as I can aswell.. Can this turn down my CPU and stuff? Theres always programs for Windows but not any that I have seen for Linux as yet.. I've been here a liddle while.. Care to explain this to me? :D

---


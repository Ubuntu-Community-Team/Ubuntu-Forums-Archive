---
title: "kubuntu wont start any more :("
date: 2007-09-19
forum: General Help
---

### Post by Uber Nooblett on 2007-09-19
I just rebooted, everything was working fine and now when I boot I just get a black screen. If I go into recovery it gets all the way to prompt, but when I type 'sudo /etc/init.d/kdm start' the screen momentarily goes black then goes back to the prompt. When I try again it tells me KDM is already running.

I have replaced the xorg.conf with the backup and still no joy. Is there anything I can do? 

JJ

---

### Post by por100pre1 on 2007-09-19
> **Uber Nooblett said:**
> I just rebooted, everything was working fine and now when I boot I just get a black screen. If I go into recovery it gets all the way to prompt, but when I type 'sudo /etc/init.d/kdm start' the screen momentarily goes black then goes back to the prompt. When I try again it tells me KDM is already running.

I have replaced the xorg.conf with the backup and still no joy. Is there anything I can do? 

JJ

```
sudo dpkg-reconfigure kdm
```

---


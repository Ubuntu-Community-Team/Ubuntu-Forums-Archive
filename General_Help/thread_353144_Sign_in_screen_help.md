---
title: "Sign in screen help"
date: 2007-02-04
forum: General Help
---

### Post by linuxmann on 2007-02-04
When i try to sign in under my account at the user sign in screen, i type in my username and password and hit enter. when i do that i becomes a blank screen and the user sign in screen shows up again. now i cannot access my account and i dont want to format the hard drive partion again (this would be a third time if i would have to). is there anyway get into my desktop and do something about it via console login? i think i installed too many things on my partion because im pretty sure it told me about freespace running out. im thinking about deleting things just as a procaution. can anybody help? if you need more info just ask me. I have Kubuntu 6.06 dapper drake

---

### Post by nikhilk on 2007-02-04
Boot into failsafe mode and do an
```
df 
```
It will show you show you how much of free space (if any) is left on the home partition.
If it is 100% full try
```
du -s ~/*
```
It will show exactly how much space each directory (under /home) is taking up. You can make a better decision yourself then.

---

### Post by bodhi.zazen on 2007-02-04
> **linuxmann said:**
> When i try to sign in under my account at the user sign in screen, i type in my username and password and hit enter. when i do that i becomes a blank screen and the user sign in screen shows up again. now i cannot access my account and i dont want to format the hard drive partion again (this would be a third time if i would have to). is there anyway get into my desktop and do something about it via console login? i think i installed too many things on my partion because im pretty sure it told me about freespace running out. im thinking about deleting things just as a procaution. can anybody help? if you need more info just ask me.

If you are out of free space, boot to the recovery mode and remove some things ...

When you boot to the recovery mode, however, you will be at a CLI.

Try starting with your trash folder, it is in /home/user_name/.Trash

Here is a guide on the CLI if needed: [http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)

---


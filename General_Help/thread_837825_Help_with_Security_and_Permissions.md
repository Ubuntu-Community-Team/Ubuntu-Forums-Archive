---
title: "Help with Security and Permissions"
date: 2008-06-22
forum: General Help
---

### Post by SyntheticShield on 2008-06-22
I just set up a laptop for my son with Ubuntu 8.04 on it and while he has no administrator rights, I would like to do all I can to keep the set up as it is.  I dont want him to access add/remove programs or synaptic to add or remove any software.  Also is there any way to lock down the settings for software like thunderbird, firefox, etc.

I also saw on  Ubuntu Christian Edition that they had a piece of parental control softare in their distro.  How would I go about getting that for regular Ubuntu?

---

### Post by macaholic on 2008-06-22
Not sure if this will help, but it offers some parental controls you mention, [http://ubuntuforums.org/showthread.php?t=805279](http://ubuntuforums.org/showthread.php?t=805279).

---

### Post by aysiu on 2008-06-22
If you go to System > Administration > Users and Groups, you can change his user type from Administrator to Desktop User, and he should then be able to modify only his own home directory.

But you don't want him to even be able to change his own Firefox settings? You'll have to use some kind of kiosk program, then. I've heard Pessulus can do this, but I've never used it.

---

### Post by SyntheticShield on 2008-06-22
Thank you both macaholic and aysiu.

I was afraid that it would take a kiosk type set up to protect the firefox settings.  I guess I'll just have to see what all he does first. I dont think it will be an issue, I was more or less trying to be proactive.

The parental controls are more important to me than anything but I was not aware the setting him to a Desktop User would work that way.  So off I go to change that permission at least.

---

### Post by aysiu on 2008-06-22
> **SyntheticShield said:**
> Thank you both macaholic and aysiu.

I was afraid that it would take a kiosk type set up to protect the firefox settings.  I guess I'll just have to see what all he does first. I dont think it will be an issue, I was more or less trying to be proactive.

The parental controls are more important to me than anything but I was not aware the setting him to a Desktop User would work that way.  So off I go to change that permission at least.
You could probably change ownership of his .mozilla folder and make it read-only for non-owners, except for the history.dat file and Cache folder.

---

### Post by SyntheticShield on 2008-06-22
Okay, I'll give that a shot and see how it turns out.  Thank you.

---

### Post by lisati on 2008-06-23
> **aysiu said:**
> If you go to System > Administration > Users and Groups, you can change his user type from Administrator to Desktop User, and he should then be able to modify only his own home directory.

But you don't want him to even be able to change his own Firefox settings? You'll have to use some kind of kiosk program, then. I've heard Pessulus can do this, but I've never used it.

Don't forget to leave at least one user with admin privileges (a parent or some other trusted individual), for stuff like system updates and repairs if anything goes wrong.

---

### Post by SyntheticShield on 2008-06-23
correct.  I have admin rights on the PC.  Ive tried to do somethings from his account, and even typing in the admin password I was not able to do certain things.  Not sure what that was about, but I let it go for another day so I could get everything set up for him.

---


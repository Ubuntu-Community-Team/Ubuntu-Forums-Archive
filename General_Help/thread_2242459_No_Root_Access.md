---
title: "No Root Access"
date: 2014-09-01
forum: General Help
---

### Post by Clellan_Wilson on 2014-09-01
Right so I have been locked out of root access after folowing [this]("https://help.ubuntu.com/community/Partitioning/Home/Moving") tutorial on how to move the home folder, I also used (chown and chmod commands) so now I am locked out of all perms could I have some help please?

---

### Post by Clellan_Wilson on 2014-09-01
Oh and Also I can't access my home folder either.

---

### Post by Impavidus on 2014-09-02
That's an excellent tutorial which I once followed myself and regularly recomment to others. If you can't access you home directory, you can't login. If you can still login, maybe the contents of your home directory are not where you expect them or they may be hidden.

We need some more information. If you can still login, open a terminal and run these commands:```
#To check whether you're in the sudo group
groups

#To check the contents of /etc/fstab
cat /etc/fstab

#To check for the existence and use of some directories suggested by the tutorial
ls -la /media/home /home /old_home

#To find what is currently mounted
mount
```post the output of the commands. It's OK if you get some errors.

If you can't login, boot to recovery mode and drop to a root shell. Then run```
#To check whether you're in the sudo group
groups your_user_name

#To check the contents of /etc/fstab
cat /etc/fstab

#To check for the existence and use of some directories suggested by the tutorial
ls -la /media/home /home /old_home

#To mount your home partition (provided it was actually moved)
mount -a

#And again find out what's in there
ls -la /media/home /home /old_home
```Maybe we can find out what is going on.

---


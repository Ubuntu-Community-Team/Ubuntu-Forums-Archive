---
title: "Session lasted less than 10 seconds..."
date: 2007-12-29
forum: General Help
---

### Post by Virgilio on 2007-12-29
Your session lasted less than ten seconds.
  There may be something wrong with your installation
  or you may be out of diskspace.

  Try logging in a failsafe session to see if you can fix this problem.
a quick search in the forums revealed that there are solutions but none worked for me if i post my xorg log maybe somebody could tell me whats wrong?

---

### Post by taurus on 2007-12-29
Are you running out of disk space?  

Boot into recovery mode from GRUB menu and look at the output of this command, especially the first line.

```
df -h
```
If it's 100% used, then you are running out of disk space.  You can clear the cache to give you some space so you can log back in again.  Then, you need to do some more house cleaning.

```
apt-get clean
shutdown -r now
```

---


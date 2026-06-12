---
title: "Annoying Sudo bug"
date: 2007-01-24
forum: General Help
---

### Post by bb002 on 2007-01-24
Time on my PC gets about 20 minutes into the future after a week. That's not the problem I have that fixed with NTP. Now if I have a sudo session going prior to NTP correcting the system time. All sudo commands ran after the time correction result in "sudo timestamp too far into the future". That's a no brainer. However the problem comes when i want to clear that  timestamp. I use```
sudo -k
```to delete the timestamp but even that command produces the "sudo timestamp too far into the future" error. The "-k" is meant to remove the timestamp entirely but as is, it only works on VALID timestamps. Now I either wait the 5-10 minutes for time catch up to the time stamp or reboot the machine entirely. Both of which have their own problems (in either case I'll forget what I was doing in the first place and rebooting forces me to close everything). Is there anyway I can make sudo ignore the timestamp ONLY for the "-k" argument or file a bug report?

If I go the bug report route. Where is the sudo bug report system even located? My knowledge of sudo doesn't contain anything of use on locating the developer's site.

Thanks in advance!

---

### Post by matthewstory on 2007-01-24
have you tried just doing a sudo touch?

---

### Post by 3rdalbum on 2007-01-24
Have you tried:

```
sudo -K
```

(capital K)?

---


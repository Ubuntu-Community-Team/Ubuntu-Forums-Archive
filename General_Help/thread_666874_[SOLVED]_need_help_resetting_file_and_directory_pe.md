---
title: "[SOLVED] need help resetting file and directory permissions"
date: 2008-01-13
forum: General Help
---

### Post by erfahren on 2008-01-13
I went by a tutorial to mount my Ubuntu /home to access it from my Xubuntu install (and vise versa)

in Xubuntu (for instance) I mounted my Ubuntu /home partition in /mnt/ubuntu_home

the commands given at the end of the tutorial to set the permissions were:
```

sudo chown -R erfahren:erfahren /mnt/ubuntu_home
sudo chmod -R 755 /mnt/ubuntu_home

```

the problem is that now I've noticed that *all* my files (even images) in my Ubuntu /home directory are now set to be excutable

I was trying to find a way to go back through and reset the files to be read/write only without going into each directory

I think I understand this to the point to know that the directories themselves need to be set to be executable in order to access them but the files themselves shouldn't be.

how can I fix this?

---

### Post by yabbadabbadont on 2008-01-13
```
sudo find /mnt/ubuntu_home -type f -exec chmod a-x {} \;
```
This will remove execute permission from *all* **files** found in, and under, /mnt/ubuntu_home.

---

### Post by erfahren on 2008-01-13
thanks! that worked well - I am using it selectively so as not to remove executable settings on files that need it (or may need it - some in the hidden directories I'm not completely sure about so I'm leaving many alone). 

thanks again

---


---
title: "read/write permissions for mounted drive"
date: 2006-12-09
forum: General Help
---

### Post by partriv on 2006-12-09
Hi,  I've mounted an additional drive, and I would like to set the read/write permissions on it so that my user can read/write to it. It is a ext3 formatted drive.  How might I do this?  Thanks!

---

### Post by taurus on 2006-12-09
You can use chmod to change permissions to wherever you mount that ext3...  Where do you mount it though?

---

### Post by partriv on 2006-12-09
it is mounted to /dev/hdd1.  I figured it was some chmodding, i just dont know what to chmod it as :)

---

### Post by taurus on 2006-12-09
/dev/hdd1 is your drive but you have to mount it somewhere!  What's the output of this command then?

```
df -h
-or-
cat /etc/fstab
```

---

### Post by partriv on 2006-12-09
right, sorry, it's mounted at /stuff.  the drive is working and what not, i can copy data to it using sudo cp, but i want my normal user to be able to read/write without sudo.  thanks!

---

### Post by taurus on 2006-12-09
```
sudo  chmod  -R  777  /stuff
```

---

### Post by partriv on 2006-12-09
worked like a charm, thanks!!

---

### Post by taurus on 2006-12-09
> **partriv said:**
> worked like a charm, thanks!!

You're welcome.

---


---
title: "Major HDD Problem..."
date: 2007-11-21
forum: General Help
---

### Post by gamersino on 2007-11-21
Here is my system setup...
80gb HDD with Win XP on it
300gb HDD with Ubuntu on it
Both attached to the same computer... 

So my problem is that on Ubuntu I'm only able to write files on the 80gb HDD, and my 300gb HDD FileSystem is unwritable in.  Y cant I write on my 300gb HDD???

---

### Post by taurus on 2007-11-21
You can only write to your $HOME directory, /home/*user*.  If you want to modify something outside of that, you need to use sudo/gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bingoUV on 2007-11-21
1. Are your  hard disks PATA or SATA? 

2. Can you mount a partition of 300GB hard disk from a live cd and write to it?

3. output of 
```

sudo /sbin/fdisk -l

```


4. output of 
```

sudo cat /etc/fstab

```

---


---
title: "Ubuntu Installation"
date: 2006-12-29
forum: General Help
---

### Post by Bider on 2006-12-29
Im currently installing linux on a friends system, and it froze at detecting the filesystems.

I dont want to lose any data, or corrupt the partitioned drive by forcing the process to terminate in the middle of installation on the live test. of ubuntu.

any suggestions?

---

### Post by taurus on 2006-12-29
Do you have an empty partition first before you attend to install Ubuntu on it?  And terminating the installer won't screw up your data on the harddrive since you haven't done anything to the harddrive, yet!

---

### Post by Bider on 2006-12-29
The partition is empty. and im installing it on a secondary drive.

---

### Post by taurus on 2006-12-29
Are you using the LiveCD?  Before you click the installer icon, open a terminal and paste the output of this command here (see if the LiveCD detects your harddrives at all)?

```
sudo fdisk -l
```

---

### Post by Bider on 2006-12-29
Yes i've tried this, the harddrives are detected. perhaps i should rerun the live cd installation, and try again. i'll let you know.

---

### Post by taurus on 2006-12-29
By any chance you've used partition magic to format the second harddrive first before you try to install Ubuntu on it?

---

### Post by Bider on 2006-12-29
Well it seems like there is a big problem.

When i canceled the process that was froze during the live test, and rebooted.
The computer would not detect any operating system available.

The live test is also bunked as i get multiple device errors during boot process.
So im pretty much at the start with no clue.

Ubuntu had wiped and partitioned it for me so i went with that liability as default before trying partition magic.

any suggestions or clues to get this back in order?

---

### Post by taurus on 2006-12-30
Are those drives PATA, SATA, or RAID?

Again, what's the output of this command from the LiveCD?

```
sudo fdisk -l
```

---

### Post by Bider on 2006-12-30
There 'RAID', Also i cant display the output as i can no longer get into starting it up.

---

### Post by taurus on 2006-12-30
You mean the LiveCD wouldn't even boot or it is having a hard time reading the drives!  Sorry but you would have some problems using RAID!!!

---

### Post by Bider on 2006-12-30
Yes the live cd wont boot into the os, it starts to load then gives multiple device errors.
No operating system is detected at load on the harddrive.

My only understand would be to format the entire drive.
Also its a custom built computer, which had xp on it so i could split it to dual boot with linux.

but neither loads now.

---


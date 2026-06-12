---
title: "PC will not boot: problem with &quot;full&quot; harddisk / device"
date: 2007-03-17
forum: General Help
---

### Post by lenn/art on 2007-03-17
After a unwanted hard reset of the pc, i ran e2fsck to check my filesystem. Then, i shut down and restarted (after a couple of hours). Now i get the following message:

[i]GDM could not write a new authorization entry to disk. Possibly out of disk space. Error: No space left on disk.

Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime, this display will be disabled. Please restart GDM when the problem is corrected.[/i]

I started up in the recovery mode and the system hangs at the following line:

*logd [2044]: error occured while writing to logfile. No space left on device.*

What can i do? What is the solution or problem? 

The pc can't

---

### Post by taurus on 2007-03-17
If you can't even boot with recovery mode, then you need to boot with the LiveCD.  Then, mount your harddrive where / is located.  Now, remove the files in /var/cache/apt/archives to free up some space.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming /dev/hda1is where your / is...)
sudo rm /mnt/ubuntu/var/cache/apt/archives/*
sudo umount /mnt/ubuntu
```
Reboot and see if your machine comes up without error message about disk space now.

---

### Post by lenn/art on 2007-03-17
Hey,

Tnx for the answer. 

I forgot to tell that i have a dualboot. I started Win (with ext3 support) and saw that N: (linux) is "out of space". Is it safe to delete in Win on the linux partition?

---

### Post by taurus on 2007-03-17
If you are using [http://www.fs-driver.org](http://www.fs-driver.org) to access Ubuntu, then it is safe to delete all the files in /var/cache/apt/archives from Windows.  Please make sure you delete files in that directory or you could trash your Ubuntu beyond repair.

---

### Post by lenn/art on 2007-03-17
> **taurus said:**
> If you are using [http://www.fs-driver.org](http://www.fs-driver.org) to access Ubuntu, then it is safe to delete all the files in /var/cache/apt/archives from Windows.  Please make sure you delete files in that directory or you could trash your Ubuntu beyond repair.

Yes, i'm using the fs-driver. 

What do you mean with the last sentence? That it isn't safe to delete more / anything else?

---

### Post by taurus on 2007-03-17
It's safe to delete /var/cache/apt/archives but be careful if you decide to delete other stuff.  You can also delete stuff in /var/backups if you wish.

Just be careful with other files/directories.

---

### Post by lenn/art on 2007-03-17
Ok, i've done that. Now, the pc starts up until the login screen. However, i can't login ... i enter my name & pw and after a few milliseconds the loginscreen returns :?

---

### Post by taurus on 2007-03-17
Boot into recovery mode from GRUB menu and post the output of this command?

```
df -h
```

p.s.  I believe when you delete something in Windows, you also need to empty the trash bin in Windows as well.

---

### Post by lenn/art on 2007-03-17
df-h says that dev/hda4 (linux) is 100% used. 

I tried this topic [http://ubuntuforums.org/showthread.php?t=371747](http://ubuntuforums.org/showthread.php?t=371747) (especially your comment ;) ). You say to use rm. But i get as a return that the dir's arent found ...

- edit: i got some help on a dutch forum:

ctrl+alt+F1 > log in > sudo killall gdm > startx 

OR (if one isn't working)
 ctrl+alt+F1 > ctrl+c > sudo startx.

---

### Post by ubu-for on 2007-03-17
> **lenn/art said:**
> After a unwanted hard reset of the pc, i ran e2fsck to check my filesystem. Then, i shut down and restarted (after a couple of hours). Now i get the following message:

[i]GDM could not write a new authorization entry to disk. Possibly out of disk space. Error: No space left on disk.

Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime, this display will be disabled. Please restart GDM when the problem is corrected.[/i]

I started up in the recovery mode and the system hangs at the following line:

*logd [2044]: error occured while writing to logfile. No space left on device.*

What can i do? What is the solution or problem? 

The pc can't

Do **NOT** use GParted to resize your root partition! It [messed up](http://ubuntuforums.org/showthread.php?p=2311238#post2311238) my home partition.

---

### Post by taurus on 2007-03-17
> **lenn/art said:**
> df-h says that dev/hda4 (linux) is 100% used. 

I tried this topic [http://ubuntuforums.org/showthread.php?t=371747](http://ubuntuforums.org/showthread.php?t=371747) (especially your comment ;) ). You say to use rm. But i get as a return that the dir's arent found ...

- edit: i got some help on a dutch forum:

ctrl+alt+F1 > log in > sudo killall gdm > startx 

OR (if one isn't working)
 ctrl+alt+F1 > ctrl+c > sudo startx.

While still in the recovery mode, run these.

```
aptitude clean
df -h
```
What is the output of the last command?

---

### Post by lenn/art on 2007-03-19
I ran df -h and as i said, the return for /dev/hda4 was that the disk was 100% used. I cleaned the packages cache (var/cache/apt/archives) in Windows and when i restarted i emptied the trash in Linux. After that, i ran e2fsck to correct some wrong data on my data disk. Now is everything working again. However, some settings and customisations are lost (like my menu) and i've to set them back.

Tnx anyway for your help! I learned a lot from your comments.

---


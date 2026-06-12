---
title: "cannot log in"
date: 2006-11-09
forum: General Help
---

### Post by dmizer on 2006-11-09
i cannot log into my system via gui or via cli.

so i booted to the recovery console to move ICEauthority, but it didn't exist.  Xauthority did however exist (side note: i'm using icewm with wdm as my login manager), so i moved Xauthority to Xauthority_old and still couldn't log in.

so i tried to add a new user and got this:
```
# adduser dmizer2                  
Adding user `dmizer2'...
Adding new group `dmizer2' (1001).
Adding new user `dmizer2' (1001) with group `dmizer2'.
Creating home directory `/home/dmizer2'.
Copying files from `/etc/skel'
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
chfn: PAM authentication failed
adduser: `/usr/bin/chfn dmizer2' returned error code 1.  Aborting.
```
i really have no idea what could have possibly happened here.  this machine has not touched the internet all day.  i've simply been using it as a terminal to vnc into my desktop machine.  it's connected directly to my desktop via a crossover cable, and i do not have any kind of internet connection sharing going on, so there were no updates.

i logged out and rebooted and logged in several times today with no issues.

i unplugged the laptop to take it over to my friend to show him how fast it booted, and much to my dismay ... no login.  all i have at this point is the recovery console.

i'm stumped, i seriously can't figure out what could possibly have gone wrong between powering down the computer and carying it across the room and turning it on.

---

### Post by dmizer on 2006-11-09
booted knoppix and did an fsck with the following results:
```
# e2fsck -f /dev/hda1
e2fsck 1.37 (21-Mar-2005)
Pass 1: Checking inodes, blocks, and sizes
Inode 3702945, i_blocks is 8, should be 0.  Fix<y>? yes

Pass 2: Checking directory structure
Inode 3702945 (/etc/pam.d/common-account) has a bad mode (00).
Clear<y>? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -7428385
Fix<y>? yes

Free blocks count wrong for group #226 (29332, counted=29333).
Fix<y>? yes

Free blocks count wrong (13463702, counted=13463703).
Fix<y>? yes


/dev/hda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hda1: 77010/7241728 files (0.7% non-contiguous), 1000813/14464516 blocks
```
still can't log in ... am i screwed?

---

### Post by taurus on 2006-11-09
When you say you can't log in, does it mean you enter your username and password but it won't except it or it just kicks back out to the GUI login screen again?

Boot into recovery mode and at the prompt, paste the output of these two commands then.

```

ls -la /home
ls -la /home/dmizer2

```

---

### Post by dmizer on 2006-11-09
taurus, thanks for the reply.

but i managed to get logged back in again.  after running fsck, i discovered that there was no longer a /etc/pam.d/common-account, so i recreated it with the following content:
```
account sufficient pam_ldap.so
account required pam_unix.so 
```
and was able to log in again.

before this, it was not accepting my password, even when ctrl+alt+f1 and attempting to log into the console without gui.

requested info ... just in case:
```
$ ls -la /home/
total 16
drwxr-xr-x  4 root    root    4096 2006-11-09 20:19 .
drwxr-xr-x 22 root    root    4096 2006-11-09 20:06 ..
drwxr-xr-x 42 dmizer  dmizer  4096 2006-11-09 22:43 dmizer
drwxr-xr-x  2 dmizer2 dmizer2 4096 2006-11-09 20:19 dmizer2
```
```
~$ ls -la /home/dmizer2
total 20
drwxr-xr-x 2 dmizer2 dmizer2 4096 2006-11-09 20:19 .
drwxr-xr-x 4 root    root    4096 2006-11-09 20:19 ..
-rw-r--r-- 1 dmizer2 dmizer2  220 2006-11-09 20:19 .bash_logout
-rw-r--r-- 1 dmizer2 dmizer2  414 2006-11-09 20:19 .bash_profile
-rw-r--r-- 1 dmizer2 dmizer2 2227 2006-11-09 20:19 .bashrc
```

---

### Post by taurus on 2006-11-09
How did you manage to remove /etc/pam.d/common-account anyway since only root can remove stuff on the system?  Therefore, be real careful with the sudo command because one wrong move, your system will be dead...

---

### Post by dmizer on 2006-11-09
i did an fsck via knoppix and it found a problem (see post 2) in pam.d/common-account ... i fixed it, and when i booted back into ubuntu, it still wouldn't let me log in.  so i booted into recovery mode, and discovered that /etc/pam.d/common-account no longer existed.  note: previous to being forced into the recovery console as a result of my not being able to log in, i had not done anything as root/sudo.

the hard drive on this computer was recently replaced.  i wonder if it might be bad?

---


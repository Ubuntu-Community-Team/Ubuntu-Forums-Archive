---
title: "Smbfs mount works with &quot;mount -a&quot; but not on boot"
date: 2007-01-04
forum: General Help
---

### Post by kcsdad on 2007-01-04
I have a Windows XP machine on the network that has a share on it.  I'm trying to mount that share in Ubuntu 6.10 using standard smbfs syntax in /etc/fstab.  I can mount the share manually from the command line without any problems.  I have tried numerous formats of the mount "syntax" in the fstab file and all see to have the same result.  The share is not mounted at boot, but if I do a "sudo mount -a" from command line the share is then mounted.

At present the last line in my /etc/fstab says:
//office/movies /mnt/movies smbfs defaults 0 0

Can someone please help me get it to mount automatically at boot.

Thanks,
Kurt

---

### Post by Dmole on 2007-01-04
for me it works when you add a password file to that line

---

### Post by kcsdad on 2007-01-04
What if you have no password on the Windows XP machine, and the share is shared out RW for everyone?

Kurt

---

### Post by MetalMusicAddict on 2007-01-04
Heres an example and a [THREAD]("http://www.ubuntuforums.org/showthread.php?t=285245") that might help if the example doesnt work.
```
[SIZE="1"]
//server/Storage	        /media/Storage          smbfs    username=user,password=password,dmask=777,fmask=777 0 0[/SIZE]
```

Dont forget to add the user from your Ubuntu box on your XP box.

---

### Post by kcsdad on 2007-01-04
Based on Dmoles advice I set up a .smbpasswd file that contained the following:

```
username=guest
password=
```

I then put the following in /etc/fstab:

```
//office/movies /mnt/movies smbfs credentials=/home/kurt/.smbpasswd 0 0
```

I rebooted and it works perfectly now.

Like I said, mounting worked fine if done from the command line using no username or password, and it worked fine in the fstab using "defaults" if I manually did a "sudo mount -a" from the command line.  But for some reason fstab wanted a username and password, even though the share is set up to allow read-write to everyone.

I can't explain it, but it works.

Thanks to everyone for their help.
Kurt

---

### Post by CoolDreamZ on 2007-10-26
To mount the share anonymously (without the need for a password) this worked for me in my peer-peer network. Entry from /etc/fstab:

```
//server/share /mountpoint smbfs username=guest 0 0
```

---


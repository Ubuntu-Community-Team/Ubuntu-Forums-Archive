---
title: "Can't get rid of Amanda from login screen"
date: 2015-06-06
forum: General Help
---

### Post by rdh61 on 2015-06-06
Hi,

The user "Amanda" has appeared on my log in screen recently, alongside myself and my wife. Nobody uses this home computer except myself. However, if my wife caught site of the login screen there could be trouble. I don't even know any Amandas! The only thing I can think of is that I recently installed the package Amanda, and then removed it, having realised it was not right for me. If I open System Tools -> Users and Groups, Amanda does not appear listed in "User Settings". Yet she's on my login screen. Please help me evict her!

Many thanks.

---

### Post by sudodus on 2015-06-06
Strange problem!  It seems that the package Amanda created a user id of the kind, that can log in. And it does not wipe it correctly, when the package is removed.

Have you tried to reboot (not only logout) and check if the Amanda user disappears?

Have you checked in the file /etc/group, if the user id amanda is there?

```
grep -i amanda /etc/group
```

---

### Post by rdh61 on 2015-06-06
Thanks for your reply. On every reboot Amanda is still on the login screen.

```
robert@robert-P4i65GV:~$ grep -i amanda /etc/group
disk:x:6:amandabackup
tape:x:26:robert,amandabackup
robert@robert-P4i65GV:~$ 

```

Is it safe for me to delete amandabackup from this file?

> **sudodus said:**
> Strange problem!  It seems that the package Amanda created a user id of the kind, that can log in. And it does not wipe it correctly, when the package is removed.

Have you tried to reboot (not only logout) and check if the Amanda user disappears?

Have you checked in the file /etc/group, if the user id amanda is there?

```
grep -i amanda /etc/group
```

---

### Post by steeldriver on 2015-06-06
Did you just remove the package(s)? or did you purge them (remove all configuration files as well)?

There's probably a postrm script that's supposed to delete the amanda user when the owning package is purged

---

### Post by rdh61 on 2015-06-06
OK, reinstalled amanda-backup-client then purged...

```
robert@robert-P4i65GV:~$ sudo apt-get purge amanda-backup-client
[sudo] password for robert:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  xinetd
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED
  amanda-backup-client*
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 5,642 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 566067 files and directories currently installed.)
Removing amanda-backup-client (3.3.7-1Ubuntu1404) ...
Purging configuration files for amanda-backup-client (3.3.7-1Ubuntu1404) ...
rmdir: failed to remove ‘/var/lib/amanda’: Directory not empty
Removing user `amandabackup' from group `tape' ...
Done.
dpkg: warning: while removing amanda-backup-client, directory '/var/lib/amanda' not empty so not removed
dpkg: warning: while removing amanda-backup-client, directory '/etc/amanda' not empty so not removed
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
robert@robert-P4i65GV:~$

```

So "purge" doesn't, in fact, purge! Anyway, I removed those two directories manually. But on reboot, Amanda is still on the login screen. Very irksome that a package will mess with one's system like this.




> **steeldriver said:**
> Did you just remove the package(s)? or did you purge them (remove all configuration files as well)?

There's probably a postrm script that's supposed to delete the amanda user when the owning package is purged

---

### Post by deadflowr on 2015-06-06
Post sudodus' command again but replace /etc/group with /etc/passwd, please.
For what it's worth.
At the very least it should give you more info on the amandabackup user.
Or any users with amanda in their name.

---

### Post by rdh61 on 2015-06-06
```
robert@robert-P4i65GV:~$ grep -i amanda /etc/passwd
amandabackup:x:63998:6:Amanda:/var/lib/amanda:/bin/bash
robert@robert-P4i65GV:~$ 
```

---

### Post by steeldriver on 2015-06-06
BTW where did you get the amanda-backup-client package and how did you install it? as far as I can see the native Ubuntu packages are amanda-common, amanda-client, and amanda-server

What does

```

dpkg -l | grep amanda

```

show?

---

### Post by deadflowr on 2015-06-06
deluser should be able to remove the user
simply 
```
sudo deluser amandabackup
```
for more on deluser
look at it's manual page in a terminal with
```
man deluser
```

Hope that helps.

**Edit**: look at the post above this first.

---

### Post by rdh61 on 2015-06-07
That's a good point. I downloaded it from [here]("http://www.zmanda.com/download-amanda.php") and installed with GDebi (without having properly researched my subject or read accompanying notes). I now realise I should have done those things, and checked to see if it was available through Synaptic first. Lesson learned. A mitigating circumstance is that I was led to that page by a link on [this]("https://help.ubuntu.com/community/BackupYourSystem") Ubuntu help page.

robert@robert-P4i65GV:~$ dpkg -l | grep amanda
robert@robert-P4i65GV:~$ 


> **steeldriver said:**
> BTW where did you get the amanda-backup-client package and how did you install it? as far as I can see the native Ubuntu packages are amanda-common, amanda-client, and amanda-server

What does

```

dpkg -l | grep amanda

```

show?

---

### Post by rdh61 on 2015-06-07
Yes, that worked, thank you very much. ):P

> **deadflowr said:**
> deluser should be able to remove the user
simply 
```
sudo deluser amandabackup
```


---


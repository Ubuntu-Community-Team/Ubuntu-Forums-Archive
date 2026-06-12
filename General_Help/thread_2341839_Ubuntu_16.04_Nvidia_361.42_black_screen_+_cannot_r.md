---
title: "Ubuntu 16.04 Nvidia 361.42 black screen + cannot remove /var/lib/dpkg/lock: Read-only"
date: 2016-11-01
forum: General Help
---

### Post by agnik on 2016-11-01
Hi,

there are some Q&A about this in the internet, but I haven't been able to solve the problem so far, maybe cause I'm new to Linux.

I had problems with update / upgrade which always got stuck on the same line[COLOR=#111111][FONT=Ubuntu]:

[/FONT][/COLOR][IMG]https://i.stack.imgur.com/xh3bS.jpg[/IMG]

Yesterday after switching my lap on I got a login page and then black screen with cursor.
I tried different solutions, but nothing worked. I have a Win10/Ubuntu dual boot, so I switched to Ubuntu advanced options and chose 'root - root to shell prompt' and tried some commands. Every time I get the same problem:[COLOR=#111111][FONT=Ubuntu]

[IMG]https://i.stack.imgur.com/bZItF.jpg[/IMG]
[/FONT][/COLOR]
```
sudo rm /var/lib/dpkg/lock
``` didn't work, I got: ```
cannot remove /var/lib/dpkg/lock: Read-only file
```

Please help - I can't work without Ubuntu and I have many files there :/

---

### Post by howefield on 2016-11-01
> **agnik said:**
> ```
cannot remove /var/lib/dpkg/lock: Read-only file
```

Once in the recovery shell try..

```
sudo mount -o remount,rw /
```

Then try your commands again.

---

### Post by Hadaka on 2016-11-01
Please also try..
```
sudo rm -rf /var/lib/dpkg/lock
sudo dpkg --configure -a
```
thanks.

---

### Post by agnik on 2016-11-01
Omg thank you very much, after running commands you suggested my Ubuntu is alive again :))))) Yeah!!!! I'm writing from Ubuntu now :))
But I don't know what do to next. I mean I don't want to get into such problem again. What to do with Nvidia? I'm afraid of update and upgrade now.

---

### Post by Hadaka on 2016-11-01
Hi, it should be ok now to run the commands, just do not do it with a root prompt #root
Bring up a regular terminal with keypress "ctrl/alt/t" then do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
 sudo apt-get autoclean
```
Thanks.

---


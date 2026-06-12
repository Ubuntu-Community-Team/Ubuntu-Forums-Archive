---
title: "[SOLVED] Removed /var/log/. How to fix?"
date: 2008-06-04
forum: General Help
---

### Post by BlackDex on 2008-06-04
Hello there,
I Did something very very wrong.
I removed the /var/log folder...

Is there a way how i can fix this???
Thx.

---

### Post by spanish07 on 2008-06-04
sorry

---

### Post by ibuclaw on 2008-06-04
Just recreate all the folders that it once held. The log files will reappear in them once you do so.

I can't give you a specific list as to what goes on in **your** log directory. But my folder can be recreated with these commands:
```

sudo mkdir -p /var/log/apparmor
cd /var/log
sudo mkdir apt
sudo mkdir cups
sudo mkdir dist-upgrade
sudo mkdir exim4
sudo mkdir fsck
sudo mkdir gdm
sudo mkdir installer
sudo mkdir news
sudo mkdir unattended-upgrades
sudo mkdir samba
sudo mkdir samba/cores
sudo chmod 700 samba/cores

```

I have a pretty standard system, so hopefully that should cover almost everything.

But be on the lookout for the odd error message in the syslogs. As it should tell you when an app is trying to write data to a non-existant folder.

Regards
Iain

---

### Post by aquavitae on 2008-06-04
Is it necessary to recreate the folders at all, or will they be created by the programs when needed?  I don't know, but I'd have thought they would.

---

### Post by BlackDex on 2008-06-04
> **aquavitae said:**
> Is it necessary to recreate the folders at all, or will they be created by the programs when needed?  I don't know, but I'd have thought they would.

That isn't the case.
Not with apache and mysql anyway.

i'm just used the script from tinivole, and now check stuff manualy, before i restart.

---

### Post by ibuclaw on 2008-06-04
> **aquavitae said:**
> Is it necessary to recreate the folders at all, or will they be created by the programs when needed?  I don't know, but I'd have thought they would.

Oddly enough, no...
I once had a problem where aptitude kept throwing error messages at be because the folder /var/log/apt didn't exist (Tried to write data to a non-existant folder).

And everytime I'd recreate it and reboot, the folder would get removed and the error messages would pop up again.

Had to put a line in my /etc/gdm/PreSession/Default file to fix it...

Iain

---

### Post by aquavitae on 2008-06-04
Weird! It sounds like it could almost be considered a bug - it would require hardly any code to just attempt to create the folder before writing it! But I suppose all programs that log there would have to implement it. Some do, some don't...

---

### Post by BlackDex on 2008-06-04
Well i fixed it.
I luckely did an updatedb a few minutes before i did this major stupid command.
So i just used 'locate /var/log' and restored all the files and folders of that result.
I Just rebooted and its all still alive :).
Thx for the help.

---


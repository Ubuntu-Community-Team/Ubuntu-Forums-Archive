---
title: "networking issues"
date: 2008-02-04
forum: General Help
---

### Post by xxrealmsxx on 2008-02-04
I am unable to access any network machines in the windows networks area on my Ubuntu 7.10 laptop.

I cannot ping my router, or my server, yet I have internet.

The only thing that has changed on my computer due to my efforts are:

I installed the ati drivers using envy and i installed but then uninstalled moblock.

I have tried changing the name of the workgroup from MSHOME to WORKGROUP (as i set in my router and my xp install says) and still no progress. The strange thing is everything worked without me changing Samba.conf before.

Also, I cannot access my router by typing in the ip address, or the web interface for my server by typing in its ip address--both of which work in Windows XP and Vista. I have even tried pinging both and have had no luck.

I have tried wired and wireless and I am also unable to access the server by ip through the "connect to server" dialog.

Is there anyway I can just set my network settings back to what they were on a fresh install?

---

### Post by pdub on 2008-02-04
Although I am not familiar with moblock, it looks like this is your problem. Are you sure that moblock is completely removed? 

```
ps -A
```

Look for moblock. 

See if the /etc/moblock.conf still exists. You might try deleting any moblock related file in /etc and then reboot.

---

### Post by xxrealmsxx on 2008-02-04
> **pdub said:**
> Although I am not familiar with moblock, it looks like this is your problem. Are you sure that moblock is completely removed? 

```
ps -A
```

Look for moblock. 

See if the /etc/moblock.conf still exists. You might try deleting any moblock related file in /etc and then reboot.

Removing the moblock folder worked, thanks a ton. 

The strange thing is i did not have problems when Moblock was installed.

---


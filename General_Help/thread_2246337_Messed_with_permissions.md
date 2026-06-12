---
title: "Messed with permissions"
date: 2014-09-30
forum: General Help
---

### Post by mayurpathak6 on 2014-09-30
Hello,

I was screwing around with the permission settings, now Ubuntu will not boot properly. Upon starting the computer, it tells me that I need to configure the graphics and other settings manually; afterwards the screen goes black. I tried booting into recovery mode and even though I am putting in the correct password (even in TTY), it tells me "can't execute /bin/bash, permission denied," or something like that. All I did was mess with the permissions, nothing else. Can someone please help me fix this problem? I'd like to be able to fix it instead of having to do a clean reinstall since I have tons of school-related stuff on this computer. I am running Ubuntu 14.04.1. Thanks in advance.

---

### Post by QIII on 2014-09-30
Hello!

"Mess with the permissions" doesn't tell us much.  Could you explain what you did?

---

### Post by mayurpathak6 on 2014-09-30
> **QIII said:**
> Hello!

"Mess with the permissions" doesn't tell us much.  Could you explain what you did?

Yes, I clicked on the icon on the right that looks like a little file-cabinet and then right-clicked on computer. Went to properties --->permissions, then changed stuff around. Changed group to something I don't remember, as well as owner. Sorry I don't really know what I did specifically as I am still fairly new to Linux, but hope this helps!

---

### Post by QIII on 2014-09-30
The first thing I would do is use a Live DVD/USB to see if you can find and access your important files.  If you can, then back them up to another medium.

You have done the sort of thing that is one of the very, very few reasons I would ever recommend a reinstallation right from the start.  When the permissions are arbitrarily and randomly changed in directories (particularly if done so recursively), there is no telling what has been affected.  Since there are literally thousands of files, some of which require particular permissions to be set for your OS to function, it could take days for even an expert to sort things all out.

Don't panic.  Just see if you can identify and access your important data.

---

### Post by mayurpathak6 on 2014-09-30
> **QIII said:**
> The first thing I would do is use a Live DVD/USB to see if you can find and access your important files.  If you can, then back them up to another medium.

You have done the sort of thing that is one of the very, very few reasons I would ever recommend a reinstallation right from the start.  When the permissions are arbitrarily and randomly changed in directories (particularly if done so recursively), there is no telling what has been affected.  Since there are literally thousands of files, some of which require particular permissions to be set for your OS to function, it could take days for even an expert to sort things all out.

Don't panic.  Just see if you can identify and access your important data.

Ok, thank you very much for the help; luckily I have a flash drive which I'll use to back my school stuff.

---

### Post by mayurpathak6 on 2014-09-30
Ok, here is an update. I ran a few live programs, but Kali Linux was the only one that allowed me to access my file system. I accessed it through Kali, and re-changed the permissions. So Ubuntu started working again (yay), but it seems like the "sudo" command doesn't work anymore in the command line. This is what I am seeing:

:~$ sudo restart lightdm
sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

I also tried alt+f2, and typed in gksu nautilus, but that does nothing.

---

### Post by mayurpathak6 on 2014-09-30
Backed up a bunch of **** and reinstalled. Just lost patience lol. But I will not **** with permissions again, until I at least become more familiar with Linux.

---

### Post by The Cog on 2014-09-30
That's the right thing to do. After messing with permissions like that, the system is pretty-much busted. Some files have special requirements as to what their permissions should be, and it is much quicker to reinstall than to try to fix them all by hand. 
I'm happy to see you saved your data.

---


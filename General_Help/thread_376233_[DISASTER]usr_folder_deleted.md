---
title: "[DISASTER]usr folder deleted"
date: 2007-03-04
forum: General Help
---

### Post by flapane on 2007-03-04
I was manually deleting a folder in /usr and for some reason I did sudo rm -r /usr/ foo/folder/damn/  
That blank space after /usr obviously deleted all my usr folder...
now what to do? I am using feisty, I booted from the last livecd and manually copied usr livecd folder in my feisty using chroot, but it seems that eth doesn't work well...
if I do something like aptitude or apt-get update it says it couldn't resolve the host packages.ubuntu.it and things like this... but if I try a ping it works and dhclient show my ip...
sounds strange, isn't it?:confused:

---

### Post by flapane on 2007-03-05
bump?

---

### Post by SyvanX on 2007-03-05
If it were me, I would just backup my home directory and reinstall, then restore my home directory to the new install.

---

### Post by flapane on 2007-03-07
it wouldn't be a bad idea, but herd5 installer gives seg.fault...
Furthermore, are there any important files I must backup in directories except than home ?

---

### Post by SyvanX on 2007-03-07
You'll have to reinstall the programs you want, but the preferences for them should live in your home directory.  The one thing to watch out for is any special configurations you have, like an Apache server configuration, or some Samba settings.

---

### Post by flapane on 2007-03-07
thanks.
Now it remains to find out why herd5 installer gives a sementation fault

---


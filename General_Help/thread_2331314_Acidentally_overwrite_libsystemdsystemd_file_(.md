---
title: "Acidentally overwrite /lib/systemd/systemd file :("
date: 2016-07-20
forum: General Help
---

### Post by mrhub on 2016-07-20
Hello.
I was trying to add a service and accidentally overwite systemd file with the new service file... :(
How the h*ll do I get it back?
Is it downloadable from somewhere?
Its a 16.04 ubuntu server.

Im afraid if I restart the machine it wont boot...

---

### Post by The Cog on 2016-07-20
Oops! All I can think of is to boot a live USB/CD and copy the file from the live in-memory filesystem to the hard disk. But that doesn't allow for any upgrades since that file was installed. Perhaps do an apt-get update and apt-get upgrade on the live system first (but not restart).

---

### Post by &amp;KyT$0P# on 2016-07-20
Like The Cog says, it's safest to boot into a live CD/DVD/USB to repair the situation.  I would suggest that, once booted in the live environment, chroot into the broken system and run these commands in the chroot shell:
```
sudo apt-get update
sudo apt-get --purge --reinstall install systemd
```

Does that fix it?

---

### Post by mrhub on 2016-07-20
Thanks for the answer, I created a Virtual mashine and upgraded it to the same version and moved the systemd file to my broken server, and rebooted (and hold my breath...) and it worked! Joy!!

---

### Post by The Cog on 2016-07-21
Excellent! 

halogen2: Thanks for the chroot + reinstall idea. I'll try to remember that.

mrhub: You can mark the thread solved in the Thread Tools pull-down menu at the top of the page.

---


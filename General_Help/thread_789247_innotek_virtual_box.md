---
title: "innotek virtual box"
date: 2008-05-10
forum: General Help
---

### Post by luckybob69 on 2008-05-10
i was trying to install this when i had a power failure now my update manager 
gives this message. Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it


and synaptic package E: the package virtualbox needs to be reinstalled but i cant find an archive for it.

E: internal error opening cache (1) Please report.   


Both the manager and synaptic will not let me do anything els until this is fixed


please can someone help thanks

---

### Post by ghost_ryder35 on 2008-05-10
have you tried fixing broken files
```

sudo apt-get --help

```
there is a command (which I can not remember off the top of my head) to fix broken things ;) run that command and then update your apt.  hopefully it helps you

---

### Post by forestpixie on 2008-05-10
do 
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

and try installing it again - had exactly the same problem once

---

### Post by luckybob69 on 2008-05-10
the terminal will not let me enter my password do you think i have a buggy copy of ubuntu ihave so many bugs like i have to restart many times for sound to work and it freeze up alot? thaks

---

### Post by The Cog on 2008-05-10
Sounds bad. A reinstall might help. Double-check your install CD first. Get the md5 sums file from the downloads page and check the CD with the command
mdsum /dev/cdrom

---

### Post by forestpixie on 2008-05-11
If you mean you can't see the password that is normal - but it is being entered.

---

### Post by unicorn_2003_1 on 2008-06-07
Well, had the same problem myself.
sudo dpkg --remove --force-remove-reinstreq virtualbox
the above line worked.

read man for the -remove-reinstreq option
thanks

---


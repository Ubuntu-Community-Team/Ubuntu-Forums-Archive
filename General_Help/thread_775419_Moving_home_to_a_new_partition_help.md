---
title: "Moving home to a new partition help"
date: 2008-04-30
forum: General Help
---

### Post by holdie on 2008-04-30
So I've tried moving my /home folder to a new partition using the psychocats guide, and everything seems to go according to plan...

however, when I try and log in after the move/telling fstab to mount my home partitionn to /home, I get an error saying that my dmrc file is being ignored and something about it needing to have 644 permissions.  It then doesn't let me go into the desktop, reloading the boot screen

I booted to the command line and switched the permissions of my /home/username folder to 777 and that allow me to get into the desktop, however that dmrc error is still there

I'd like to get rid of it, not to mention I know that having 777 permissions for your home folder isn't the greatest idea...anyone think they can help me?

thanks

---

### Post by ryanhaigh on 2008-04-30
Open a terminal and put in the following
```

chmod 644 ~/.dmrc

```
You might also want to revise the permissions you have given to your entire home contents because now everyone can read and write.

---


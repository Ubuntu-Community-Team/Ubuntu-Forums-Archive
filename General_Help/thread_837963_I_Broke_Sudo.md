---
title: "I Broke Sudo"
date: 2008-06-23
forum: General Help
---

### Post by gerowen on 2008-06-23
Ok, I broke sudo.  I did a chmod on /etc/sudoers instead of the /etc/sudoers.backup that I made on accident.  Well the file permissions never changed, when I look at it in Nautilus it still says root on everything, but none of my programs that require root permissions, to include synaptic, will start up, and when I trying running something with sudo in the command line I get:

```
sudo: /etc/sudoers is mode 0777, should be 0440
```

Well seeing as there is no root user for me to become in order to fix this, does this basically mean I need to reinstall Ubuntu?

---

### Post by sdennie on 2008-06-23
Reboot into recovery mode (it's an option in grub but, you may have to hit escape as the machine restarts to choose it) choose the options that gets you into the command line (I think it's called "root") and then type:

```

chmod 0440 /etc/sudoers
exit

```

Continue with normal boot process.

---

### Post by paulderol on 2008-06-23
you might try making a new user and copying the file over in place of the other? that might work. 

i accidentally chowned my whole filesystem at one point, and had to begin again. just backup your important data and make an apt-on-cd for the rest of it and you should be able to recover if you can't get it to repair.

---

### Post by gerowen on 2008-06-23
Ah the root terminal in recovery mode worked, I didn't know about that little option, I've never had to use it before, thanks.

---


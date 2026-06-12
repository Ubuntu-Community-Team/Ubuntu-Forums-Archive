---
title: "x goes blank and tty1,2,3,4,5,6 give login"
date: 2013-03-06
forum: General Help
---

### Post by pipesbi on 2013-03-06
Greetings,
Problems with 12.04.2 LTS.  I've reinstalled 3 time on different dell hardware (laptops).  When system screen locks I can't get back to x, ssh sessions won't work either.  I can get to tty and have a login screen, but each time I  try to put a user in I don't get an opportunity to put a password in, just goes back to login?  It seems the only way I can get out of this state is to power down the system which reboots into a kernal panic and all is dead and requires a reboot. 

Any suggestions on how I can safety reboot of get something out of one of the tty?

thx,,

---

### Post by ibjsb4 on 2013-03-06
> **pipesbi said:**
> Any suggestions on how I can safety reboot of get something out of one of the tty? thx,,

```
sudo reboot
```

Is this a server install?  Are you trying to use startx?

---

### Post by pipesbi on 2013-03-06
> **ibjsb4 said:**
> ```
sudo reboot
```

Is this a server install?  Are you trying to use startx?

X has frozen so I go out to other ttys and get a login.  However, whenever I put something in the login nothing gets accepted.  E.g. sudo reboot just comes back to the login....it's like some kind of loop?

thx,
Bill

---

### Post by ibjsb4 on 2013-03-06
A reboot will take you back to tty if this is a server install, thats why I asked.  If this is a desktop install maybe try reinstalling your display manager, see if that helps or see if you have any broken packages.

Display manager
```
sudo apt-get install --reinstall lightdm
```

Fix broken packages
```
sudo apt-get -f install
```

---

### Post by cortman on 2013-03-06
Could be your .Xauthority is owned by root- run

```
ls -al | grep .X
```

while in your home directory. Check the permissions- you should have it should be rwx all around. If not you should change ownership of it-

```
chown username:username .Xauthority
```

---

### Post by pipesbi on 2013-03-06
Can't run any commands from tty, I seemed to be doomed to recycle power which give kernel panic and then I'm not sure what I can do from grub?

---

### Post by ibjsb4 on 2013-03-06
Do you have any older kernels in grub?  Try one.

---

### Post by pipesbi on 2013-03-06
older kernels exist but, from multiple installs related to this problem.  Any command option from GRUB which may help me fix issues?

thx for the help

---


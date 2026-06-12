---
title: "Root user messed up"
date: 2008-01-16
forum: General Help
---

### Post by Bruut on 2008-01-16
I just installed Ubuntu gutsy server on a machine here. But while trying to add a group to the default user (tts), I messed it up. If I wan't to do a sudo ls (for example)

```
[B]
tts@webserver:~$ sudo ls
tts@webserver:~$
[/B]
```

This happens with all sudo commands, even sudo su. It doesn't do anything, doesn't even ask for a password. 

groups tts outputs:

```
[B]
tts@webserver:~$ groups tts
tts : tts www-data
[/B]
```

can this be easily fixed? or is it easier to reinstall ubuntu. 

There are no other users created on the system.

I couldn't find similar topics about this problem.

---

### Post by Joeb454 on 2008-01-16
What about if you run ```
groups root
```

Root should still be in there

---

### Post by Bruut on 2008-01-16
```

tts@webserver:~$ groups root
root : root

```

---

### Post by Joeb454 on 2008-01-16
Ok just checking root's still there :)

So what exactly happens if you try and run a command with sudo in it? or su or gksu?

---

### Post by Bruut on 2008-01-16
Exactly as I posted, it immediatly goes to the next line, whatever I type

```

Last login: Wed Jan 16 14:43:46 2008 from 10.0.0.171
tts@webserver:~$ sudo dsjkladnsa
[sudo] password for tts:
tts@webserver:~$ sudo fdsmlnmee
tts@webserver:~$ sudo su
tts@webserver:~$ sudo j2393rtfre5 fd5t 34sfds
tts@webserver:~$

```

I have to admit, it _does_ ask for a password. But it does nothing with the command. Looks like its just ignoring everything after sudo.

---

### Post by Joeb454 on 2008-01-16
Well I can't tell you for sure that it does nothing with the command, because you didn't use a proper command :p

---

### Post by aysiu on 2008-01-16
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by bodhi.zazen on 2008-01-16
You need to boot to recovery mode and add your user to the admin group.

And possibly others

IMO, I do this with :

```
nano /etc/group
``` and add your user(s) at the end of the admin line (and other groups you want)

Then Ctrl-X to exit, type Y to save

reboot

---

### Post by Bruut on 2008-01-16
Ok thanks for the help. i'll give it a try.

[edit]

It worked, editing the /etc/group file is far more easier than struggling with usermod

---


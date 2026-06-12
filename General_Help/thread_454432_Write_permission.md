---
title: "Write permission"
date: 2007-05-25
forum: General Help
---

### Post by burt_57 on 2007-05-25
Why don't I have write permission to 
/usr/local/game
Can that be fix , and how?
Am trying to install Max Payne and it want to install their.
Am using max.payne_105-english-2.run for install.

Burt

---

### Post by Metacarpal on 2007-05-25
Are you double-clicking the file to install it, or are you running the command from a terminal (Applications menu > Accessories > Terminal)?

The best way to do this would be to run it in terminal, with "sudo" before the command.  That will allow you to install it more-or-less as root, which will be able to write to /usr/local/games

example: if the installer is on a cd-rom:
```
sudo /media/cd-rom/max.payne_105-english-2.run
```

---

### Post by frafu on 2007-05-26
Hello, 

I have moved this thread to the General Help Forum, where it is more appropriate. 

Have a nice day.

---

### Post by taurus on 2007-05-26
> **frafu said:**
> Hello, 

[COLOR="Blue"]I have moved[/COLOR] this thread to the General Help Forum, where it is more appropriate. 

Have a nice day.

:confused:

---

### Post by earobinson on 2007-05-26
> **frafu said:**
> Hello, 

I have moved this thread to the General Help Forum, where it is more appropriate. 

Have a nice day.
Was that in the wrong thread?

---

### Post by frafu on 2007-05-26
This thread had originally been posted into the Accessibility Forum, which is normally used for discussion about disability related software. Don't bother about it anymore... 

Sorry, I should have been more clear. 

bye

Francesco

---

### Post by burt_57 on 2007-05-26
> **taurus said:**
> :confused:
I did notice that after I post.
Me bad ;)

---

### Post by burt_57 on 2007-05-27
> **Metacarpal said:**
> Are you double-clicking the file to install it, or are you running the command from a terminal (Applications menu > Accessories > Terminal)?

The best way to do this would be to run it in terminal, with "sudo" before the command.  That will allow you to install it more-or-less as root, which will be able to write to /usr/local/games

example: if the installer is on a cd-rom:
```
sudo /media/cd-rom/max.payne_105-english-2.run
```
That installer is in /home/robert that is where it install itself when I downloaded it :(

---

### Post by Metacarpal on 2007-05-27
then use:

```
sudo /home/robert/max.payne_105-english-2.run
```

---


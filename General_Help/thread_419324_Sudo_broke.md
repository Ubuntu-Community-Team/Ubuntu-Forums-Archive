---
title: "Sudo broke"
date: 2007-04-22
forum: General Help
---

### Post by montgoss on 2007-04-22
Commands run with sudo don't do anything.  They don't give an error, but they also don't actually do the action.

I first noticed this when trying to unmount something.  I put "sudo umount /media/hdb1" and it prompted me for the password and appeared to successfully execute the command.  However, the drive was still mounted.  I tried other things as well (chown, chmod, etc.), and nothing works.

If I first go into su, then run the same command (without sudo), it works just fine.  What's wrong?

---

### Post by Valdrone on 2007-04-22
I know this sounds like a stupid thing, but are you using the Super User Terminal?

Also, which terminal app are you using?

---

### Post by montgoss on 2007-04-23
I'm using gnome-terminal.  I'm not sure what you mean by "Super User Terminal".  The command/shortcut I run to get a terminal is just "gnome-terminal".

---

### Post by taurus on 2007-04-23
What happens if you run this command from a terminal (post the output here)?

```
sudo aptitude update
```

---

### Post by ulli.winter on 2007-04-26
same problem here...
it really does nothing....

"ulli@ullin-laptop:~$ sudo aptitude update
Password:
ulli@ullin-laptop:~$ 
"

---

### Post by ulli.winter on 2007-04-26
ok.... according to [http://ubuntuforums.org/showthread.php?t=421176&page=2](http://ubuntuforums.org/showthread.php?t=421176&page=2) the user account has to be in adm and admin group...
i solved the problem with the instruction there.....

---


---
title: "messed up resizing of fat32 partition and SSH question"
date: 2007-05-17
forum: General Help
---

### Post by dfreer on 2007-05-17
My laptop crashed on me in the middle of an SSH session to my server, where I was resizing my FAT32 partition using parted. Is there an easy way to run an SSH command as if from the local machine, so that if my SSH session gets disconnected the command will still run?

Also, although my data *appears* to be intact (partition size still reports as 129 GB's instead of the 50 GB's I was resizing it to), should I be very, very worried? can/should I resume resizing?

---

### Post by dexter on 2007-05-17
> **dfreer said:**
> My laptop crashed on me in the middle of an SSH session to my server, where I was resizing my FAT32 partition using parted. Is there an easy way to run an SSH command as if from the local machine, so that if my SSH session gets disconnected the command will still run?

You could use screen, a beautifull peace of software. 
Type "screen command" to run command in a new screen, you can close your terminal now, play some ping pong or whatever you like, ... when logging in over ssh again, type "screen -x" and you will attach to the session you started earlier. You can even have multiple screen sessions at a time. It takes some time to get used to it, but it can make life a lot easier.

> 
Also, although my data *appears* to be intact (partition size still reports as 129 GB's instead of the 50 GB's I was resizing it to), should I be very, very worried? can/should I resume resizing?
You could try resuming. Making a backup first would be wise though.

---

### Post by carlosqueso on 2007-05-17
If you want to use screen, [http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen) is a good tutorail.  Of course, ignore the parts about installing, as you don't have a gentoo system.

---

### Post by dfreer on 2007-05-17
> **dexter said:**
> You could use screen, a beautifull peace of software. 
Type "screen command" to run command in a new screen, you can close your terminal now, play some ping pong or whatever you like, ... when logging in over ssh again, type "screen -x" and you will attach to the session you started earlier. You can even have multiple screen sessions at a time. It takes some time to get used to it, but it can make life a lot easier.


You could try resuming. Making a backup first would be wise though.

Thanks for the screen info, looks awesome!

how would i go about resuming, I assume it's a command in parted? it would'nt be as simple as:
resume resize /dev/sda1
would it?

EDIT: or did you mean simply repeat the resize /dev/sda1 command :p

---

### Post by dfreer on 2007-05-19
Ok, got it working out! 
Basically, I just moved my data off and then wiped the whole thing. But I did check beforehand, it seems like resizing it still works, although it starts over again rather than resuming (not sure if it just didn't commit the changes or what). 
the screen commands works great in case I accidenlty close the terminal (thanks for that!), but doesn't seem to help if I have to hard reboot :( any other suggestions?

---


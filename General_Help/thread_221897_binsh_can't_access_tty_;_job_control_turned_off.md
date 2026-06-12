---
title: "/bin/sh: can't access tty ; job control turned off"
date: 2006-07-24
forum: General Help
---

### Post by CameronCalver on 2006-07-24
When i boot up my computer recently after grub when is loading ubuntu it comes up the error


```
/bin/sh: can't access tty ; job control turned off

```

and then i cant do anything else does anyone know how to fix it

and also i have been having alot of troubles lately people have been saying there is something wrong with my menu.lst do you want me to post it

---

### Post by Christmas on 2006-07-24
I don't know the answer but a yahoo search gave me this: [http://www.linuxquestions.org/questions/showthread.php?t=462465&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty+%3B+job+control+turned+off]("http://www.linuxquestions.org/questions/showthread.php?t=462465&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty+%3B+job+control+turned+off") and this: [http://www.linuxquestions.org/questions/showthread.php?t=462877&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty+%3B+job+control+turned+off]("http://www.linuxquestions.org/questions/showthread.php?t=462877&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty+%3B+job+control+turned+off"). Hope it will help.

---

### Post by CameronCalver on 2006-07-25
ok once i got to chroot /mnt/debian /bin/bash 

which i did chroot /mnt/temp /bin/bash instead of debian it gave this error

Bash:groups command not found
but i know what it is trying to do set the root home to the mounted hd so i can reinstall udev is there any other way i can do that
but i think we on the right track

---


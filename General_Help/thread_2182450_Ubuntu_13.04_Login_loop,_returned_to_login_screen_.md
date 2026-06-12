---
title: "Ubuntu 13.04 Login loop, returned to login screen after entering correct password"
date: 2013-10-21
forum: General Help
---

### Post by Matt Pellegrini on 2013-10-21
I'm currently unable to log in, although my password is correct.
I CAN ssh into the machine while it sits at the login screen, so the password is correct. 
I CAN also log in a guest no problem. So it's not a general problem with the graphics.

When I try to log in, the screen flashes black, then shows the nVidia splash, then loads the log in page.

I have tried:
removing /home/user/.Xauthority
reinstalling xorg and lightdm

.Xauthority has user ownership.

Also please note that due to being unable to get tty by ctrl alt f(n) - a long standing problem for my machine. The two ways I can access my machine are:
ssh into machine while it sits at log in screen
recovery mode
(also as a guest, though not particularly helpful)

I'm in quite urgent need of help here, thanks in advance for any help.
Matt

---

### Post by neutron68 on 2013-10-26
I just diagnosed and solved this problem on a Mythbuntu 12.04 system.
[http://ubuntuforums.org/showthread.php?t=2183812](http://ubuntuforums.org/showthread.php?t=2183812)

I SSHed into the machine and changed the owner AND group to the username (as it is in a normally working system)

> cd /home/username
chown username:username .Xauthority 

See if your .Xauthority file has both the owner and group set to the username:
> ls -la /home/username

---


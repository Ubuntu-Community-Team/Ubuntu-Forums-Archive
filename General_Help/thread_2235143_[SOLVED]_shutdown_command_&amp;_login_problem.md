---
title: "[SOLVED] shutdown command &amp; login problem"
date: 2014-07-19
forum: General Help
---

### Post by erciaina on 2014-07-19
Hi ubuntuers,
i have a problem with ubuntu 13.04. When i go to sleep on my laptop I always use the command "sudo shutdown -h hh:mm". I use last night but before the setted time was reached the battery is discharged. This morning, when i turn on laptop, beside my username, the login window shows this red message " The system is going down for halt in 1 min". It seems that ubuntu was trying to complete the shutdown task. 
The problem is that i can not login or do anything and "1 min" is a fake...nothing changed after 10 minutes..
I can't:

- login
- type password
- login with guest user

I try:

- to login in other tty but when i type "myusername" and enter, the system says again " The system is going down for halt in 1 min" and then come back to "Login:   "

- to reboot and open a root command shell. My /home/myusername stuff was still there and i try:

             --   to make another "shutdown -h hh:mm" or "shutdown -h now" but it does not shutdown anything..wait for a long time but nothing...

             --  to change myusername password with command "passwd myusername", it asks for new password twice but then says something                        about "token not valid" and the password remains unchanged

This situation is paradoxical !! 
Can you help me?? I don't know any other trick...

---

### Post by bapoumba on 2014-07-19
13.04 has reached EOL on January 27, 2014. you should really consider moving to a supported release.

---

### Post by steeldriver on 2014-07-19
You could try

```

mount -o remount,rw
shutdown -c

```

from the root shell

```

-c     Cancels a running shutdown.

```

---

### Post by erciaina on 2014-07-19
Finally i solved with another temp problem :)
In root comm shell i tried the command "halt",it does not worked and the system freeze. I turn off by power switch and at next reboot all seems ok and everything works fine..
I don't know what's happened but it's solved..LOL

---


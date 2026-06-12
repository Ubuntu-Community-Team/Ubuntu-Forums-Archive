---
title: "can't run samba server"
date: 2020-05-05
forum: General Help
---

### Post by abdullahtamimi on 2020-05-05
Hello,
when I type this command:
```
sudo service samba restart
```

I get this result:
```
Failed to restart samba.service: Unit samba.service not found.
```

And when I type this command:
```
sudo service smbd restart
```

I get nothing!!!

what's wrong here? how can I fix that?

---

### Post by TheFu on 2020-05-05
Perhaps installing samba is needed?

---

### Post by Tadaen_Sylvermane on 2020-05-06
I don't know anything about the service command. 

```
sudo systemctl restart smbd
sudo systemctl restart nmbd
```

Is what I usually do. Haven't had an issue yet.

---

### Post by TheFu on 2020-05-06
Tadaen, 

"**service**" is what we used before systemd was forced onto us.  Someone created a wrapper with a replacement *service* command to maintain backwards compatibility with the prior solution.  I still miss the /etc/init.d/ solution, but whatever. Guess backwards compatibility can only go so far.

Changing an interface just for the sake of change is rude to users and admins.

---

### Post by Morbius1 on 2020-05-06
> **abdullahtamimi said:**
> 
And when I type this command:
```
sudo service smbd restart
```

I get nothing!!!

what's wrong here? how can I fix that?
That is what is supposed to happen if the restart completed successfully. It's a Linux thing. You will only get output after running a command if all H-E-Double Hockey Stick happened. I'm sure there is an exception but in general only Windows gives the user positive feedback if they did something correctly.

If you want to find out if smbd is running use "status":

```
sudo service smbd status
```
Or this way:
```
sudo systemctl status smbd
```

*I really wish they had kept the order the same. After years of doing it the "service" way I keep on running "sudo systemctl smbd status".*

---


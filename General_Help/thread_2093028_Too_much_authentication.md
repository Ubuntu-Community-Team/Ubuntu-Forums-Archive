---
title: "Too much authentication"
date: 2012-12-09
forum: General Help
---

### Post by ouzie on 2012-12-09
please can sone one tell me .. why in Heavens does one ALWAYS , i mean always have to get bugged by authentications.. i try to install a software, i get stopped because i do not have authentication. CAN SOME ONE TELL ME where do i get this so called authentication. AND WY do the linux Ubuntu people have to stick to this rather anoying geek. I have installed and uninstalle dmany an UBUNTU SOFTWARE .. AND ENDING UP IN FRUSTRATION,and really just THROWING ubuntu OUT

---

### Post by Old_Grey_Wolf on 2012-12-09
I think you should read this sticky from the Security Discussions subforum, [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=1486138").

---

### Post by The Cog on 2012-12-09
The authentication you need is just your password - the one you use when you log in. If that doesn't work for you, we need to know the details on how you are trying to install the software.

This is all part of normal unix/linux security, and it is slowly coming to windows too. I think you will need to get used to it.

---

### Post by na5h on 2012-12-09
Actually, Windows users have to type in the administrator password as well when doing changes to the system these days...but many Windows users are logged on as the system administrator all the time (since that is the first and for many people, only account that they ever create).

It is advisable to have a separate account without administrator rights in Windows as well. That way, viruses won't get full access to the system in case your computer gets infected. Common tasks can still be performed by tapping in the administrator password.

---

### Post by Old_Grey_Wolf on 2012-12-09
> **ouzie said:**
> ...CAN SOME ONE TELL ME where do i get this so called authentication...

> **ouzie said:**
> ...I have installed and uninstalle dmany an UBUNTU SOFTWARE .. AND ENDING UP IN FRUSTRATION,and really just THROWING ubuntu OUT...

These two statements seem to be contradictory. How did you install software without knowing how to get authorization? 

The separation of user accounts and the root account is one reason that Linux does not get compromised by malware very often.

---

### Post by Tolleywood on 2013-01-25
I'm having the same problem with this authentication thing.  Just installed the 32-bit version as a stand-alone and still trying to sort out what I'm doing with this system. 

Anyway, when I get to that authentication page and enter my password, it shows as an error.  If I go back to check my administrator settings, my password doesn't work there either.  I've set this up as an auto login, so there shouldn't (?) be any password issues there..........  So apparently I somehow changed my administrator password without knowing that I did. 

Do I have to reload and go thru the setup again to get around this?   Or is there a thread somewhere to help me thru this mess?

---

### Post by Adam_GUI on 2013-01-25
Ubuntu doesn't traditionally use Administrator (root) account login.

If you're prompted for password action during program install (launching synaptic), your regular account password should work.

If you're getting a message stating that you need administrator access to perform an action, rerun the command with gksudo.

Instead of simply running "synaptic"
Run "gksu synaptic".

You'll be prompted for a password.  Your normal account password should be all you need to provide.

RUNNING THINGS WITH GKSU CAN BE DANGEROUS!  
YOU WILL HAVE PERMISSIONS IN ALL PROGRAMS TO READ/WRITE/EXECUTE/DELETE.  EVEN CRITICAL SYSTEM FILES!
ALWAYS BE EXTRA CAREFULL WHAT YOU'RE DOING OR YOU CAN SERIOUSLY BREAK THINGS!

---

### Post by sdowney717 on 2013-01-25
[http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html)

```
sudo visudo

Find the line that says

%admin ALL=(ALL) ALL

and change it to

%admin ALL=(ALL) NOPASSWD: ALL
```

have not tried it myself

---

### Post by sdowney717 on 2013-01-25
seems to work, still have to type
gksu synaptic
but it did not ask for the pesky password.

---

### Post by lisati on 2013-01-25
The preferred method of authentication and granting superuser privileges in Ubuntu is with the sudo command and its variants. Disabling password authentication requires you to take extra precautions so that things don't get messed up by accident and thus turn into a major pain to fix.

For more information, please read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Edit: Please also take the time to read [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Thread closed.

---


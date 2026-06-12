---
title: "How do you modify Shutdown time?"
date: 2020-04-27
forum: General Help
---

### Post by vmsman on 2020-04-27
I have one Ubuntu 20.04 system that when I initiate a shutdown from the menu and choose the "Power Off" option, the system takes exactly a minute to shutdown.  I remember old versions of Ubuntu having a prompt that would come up and ask if you want to shutdown immediately or it counted down and did the shutdown.  When I choose the Power Off option from the menu on this particular system, there are no signs it accepted the command and I can access the system for right at 1 minute and then it performs a shutdown.

To avoid the wait, I simply do a command line shutdown.  I'd rather be able to use the built in command.  This problem started in 18.04 LTS and persists in 20.04 LTS.  I did not have the problem on this system in 16.04.  I have four other Ubuntu systems and none of them have this issue.  I have pretty much put up with this for a couple years now, but since this is my main system, it would be great to fix this.  

I've hunted around for any errant settings in dconf-editor to no avail and I have hunted for any scripts that might exist.  It's pretty much like I initiate the power-off and then i just return to the desktop for 60 seconds with no other options.

Does anyone have any ideas?  I'm a bit embarrassed because I have run Ubuntu since 6.04 and have always been able to work out all solutions, until now.

---

### Post by ActionParsnip on 2020-04-27
You can make it shutdown ASAP with:

```

sudo shutdown now

```

This will avoid the wait. You can specify your own wait time as long as you need
[https://linux.die.net/man/8/shutdown](https://linux.die.net/man/8/shutdown)

---

### Post by CelticWarrior on 2020-04-27
> **ActionParsnip said:**
> You can make it shutdown ASAP with:

```

sudo shutdown now

```

This will avoid the wait. You can specify your own wait time as long as you need
[https://linux.die.net/man/8/shutdown](https://linux.die.net/man/8/shutdown)

This is what the OP has been doing:
> To avoid the wait, I simply do a command line shutdown. 

---

### Post by ActionParsnip on 2020-04-27
Possibly this
[https://learnubuntumate.weebly.com/reduce-shutdown-time.html](https://learnubuntumate.weebly.com/reduce-shutdown-time.html)

---

### Post by ActionParsnip on 2020-04-27
[https://askubuntu.com/questions/1057271/change-shutdown-confirmation-timer](https://askubuntu.com/questions/1057271/change-shutdown-confirmation-timer)

---


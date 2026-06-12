---
title: "Ubuntu 12.04 will not shutdown; it hangs"
date: 2013-05-09
forum: General Help
---

### Post by mimi314159 on 2013-05-09
Hi guys,

I'm brand new to the forums!  I am running a fresh install of Ubuntu 12.04 LTS, and now my computer will not shutdown with regularity.  (Sometimes it shuts down, usually it hangs on the Ubuntu screen with one or no dots colored orange.)  Restart seems to work well most of the time (as in that only hung once).

I tried going to the safe mode to start and reboot from there; that seems to shutdown just fine.

From the regular (non-safe) version of 12.04, I tried typing in

```
sudo shutdown now
```

and could see that shutdown froze on the error

```
modem-manager[3672]: <info> ModemManager (version 0.5.2.0) starting...
modem-manager[3676]:  Could not get the system bus.  Make sure the message bus daemon is  running!  Message: Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
...
modem-manager[3696]: <info> ModemManager (version 0.5.2.0) starting...
modem-manager[3696]: Could not get the system bus.  Make sure the message bus daemon is running!  Message: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory.
```

This second error repeated 4 times, then stopped.  

I used to have Ubuntu 11.10, and it shut down just fine.  I'm running this on a Toshiba Satellite computer.  Side note--my wifi is also really buggy, and it causes a hard freeze.  This has been a persistent problem even on 11.10, so I'm not sure it's relevant, but I thought I'd mention it.

Is there some sort of package I should install?  I've run ```
sudo apt-get update
```, so my version should be current. Thanks!

---

### Post by dino99 on 2013-05-09
use :
>  sudo shutdown -h now

if network-manager is faulty with your hardware, wicd is a good replacing candidate

---

### Post by 25tom on 2013-05-09
> I've run ```
sudo apt-get update
```, so my version should be current. Thanks!

Running ```
sudo apt-get update
``` is not sufficient to update your system, only the list of available software. You need to run ```
sudo apt-get dist-upgrade
``` as well, if I'm not mistaken. I usually do it via GUI, so I'm not 100% sure of the command.

---

### Post by mimi314159 on 2013-05-09
> **25tom said:**
> You need to run ```
sudo apt-get dist-upgrade
``` as well.

Will this update my version of Ubuntu?  I think I need to stay on 12.10 LTS because 13.04 does not work with my ethernet card, for some reason.  (Separate issue.)

---

### Post by mimi314159 on 2013-05-09
Thanks; I'll give that shutdown command a try.

---

### Post by BlinkinCat on 2013-05-09
> **mimi314159 said:**
> Will this update my version of Ubuntu?  I think I need to stay on 12.10 LTS because 13.04 does not work with my ethernet card, for some reason.  (Separate issue.)

Just to let you know - Ubuntu 12.04.2 is the LTS Version


[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Edit: Added info

---

### Post by mimi314159 on 2013-05-09
> **dino99 said:**
> use :


if network-manager is faulty with your hardware, wicd is a good replacing candidate

I tried ```
sudo shutdown -h now
``` twice, and it hung the first time, but not the second.  The second time I had not been using my system for a long period of time.  It seems like my system is more likely to hang if I have spent a long time using Ubuntu.

  Any other suggestions?  And how would I start using wicd?  Is that something I install via the synaptic package manager?

---

### Post by mimi314159 on 2013-05-09
So I'm actually running 12.04 LTS...  :oops:

---

### Post by gifford on 2013-05-09
I had the problem off and on again when running Ubuntu 12.04.1. When I installed 12.04.2 it went away with the new 3.5.0 kernel.
This is the solution I used that worked for a while on 12.04.1
[http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)

---

### Post by CharlesA on 2013-05-09
> **mimi314159 said:**
> So I'm actually running 12.04 LTS...  :oops:

Title changed.

---


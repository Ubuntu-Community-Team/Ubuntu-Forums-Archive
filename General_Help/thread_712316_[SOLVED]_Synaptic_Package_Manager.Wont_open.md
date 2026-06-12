---
title: "[SOLVED] Synaptic Package Manager.Wont open"
date: 2008-03-01
forum: General Help
---

### Post by Dave Otter on 2008-03-01
I go to Systems-Admin-Synaptic Package Manager but it will not open
    I get message  dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
   Step by step--How do I do that?


                          Thanks

---

### Post by Rocket2DMn on 2008-03-01
Open a terminal from Applications->Accessories->Terminal
then run
```
sudo dpkg --configure -a
```
Then just type out your password (it will not show *'s or anything but it is accepting it).  Press enter when finished with password.

---

### Post by Dave Otter on 2008-03-01
I have done as you suggest but cant get beyond a Blue Screen asking me sor a serial Number ??

---

### Post by taurus on 2008-03-01
Are you trying to install VMware or something?

---

### Post by Rocket2DMn on 2008-03-01
> **Dave Otter said:**
> I have done as you suggest but cant get beyond a Blue Screen asking me sor a serial Number ??

Serial number?!?  There are no serial numbers in Ubuntu...  As taurus asked, are you running a virtual machine or some other proprietary software under linux?

---

### Post by Dave Otter on 2008-03-01
Trying to upgrade from Gutsy to H but get message as above trying to open Synaptic

---

### Post by Rocket2DMn on 2008-03-01
Can you please post the output when you run the command:
```
sudo dpkg --configure -a
```

Also, how did you go about trying to upgrade to Hardy?  Normally you should wait until Hardy is officially released since it is still in the Alpha stages and is unstable.  If you're set on it, you should look here: [https://wiki.ubuntu.com/HardyHeron/Alpha4](https://wiki.ubuntu.com/HardyHeron/Alpha4)

---

### Post by Dave Otter on 2008-03-01
When I type in command as you suggest the terminal goes through a process until it stops and asks for a serial no.
                   THIS SEEMS A BAD IDEA SO I WILL STOP

                            MANY THANKS TO YOU BOTH FOR ALL YOUR HELP

---

### Post by Rocket2DMn on 2008-03-01
I..... have no idea what this serial number is man.  If you're willing, you may just want to try a fresh install of Hardy if that is what you really want.
Good luck.

---


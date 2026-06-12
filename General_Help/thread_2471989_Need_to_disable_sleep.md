---
title: "Need to disable sleep"
date: 2022-02-15
forum: General Help
---

### Post by takeawaydave on 2022-02-15
I have Ubuntu 18.04.6 LTS running on a Dell Optiplex machine.

A few years ago I configured it to sleep every 2 hours. Now I need it to never sleep however can‘t for the life of me remember how to do this.

Could some please help me and provide details on how I can configure it to never sleep.

---

### Post by Jaxilian on 2022-02-15
Hi, look at this link [https://askubuntu.com/questions/1062369/how-to-disable-auto-sleep-in-ubuntu-18-04](https://askubuntu.com/questions/1062369/how-to-disable-auto-sleep-in-ubuntu-18-04)

---

### Post by takeawaydave on 2022-02-15
Thanks @jaxilian unable to run Tweak Tool since I am running without graphical interface. I&#8216;ve tried the following:
[https://www.tecmint.com/disable-suspend-and-hibernation-in-linux/](https://www.tecmint.com/disable-suspend-and-hibernation-in-linux/)
Waiting to see if this helps.

---

### Post by takeawaydave on 2022-02-15
Ok that didn&#8216;t work

---

### Post by #&amp;thj^% on 2022-02-15
> **takeawaydave said:**
> Ok that didn‘t work

Show the result of:
```
systemctl status sleep.target
```
Like:
```
systemctl status sleep.target
&#9675; sleep.target - Sleep
     Loaded: loaded (/usr/lib/systemd/system/sleep.target; static)
     Active: inactive (dead)
       Docs: man:systemd.special(7)

```
All right then to disable:
```
 sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```
Result:
```
Created symlink /etc/systemd/system/sleep.target &#8594; /dev/null.
Created symlink /etc/systemd/system/suspend.target &#8594; /dev/null.
Created symlink /etc/systemd/system/hibernate.target &#8594; /dev/null.
Created symlink /etc/systemd/system/hybrid-sleep.target &#8594; /dev/null.

```
Now:
```
systemctl status sleep.target
&#9675; sleep.target
     Loaded: masked (Reason: Unit sleep.target is masked.)
     Active: inactive (dead)

```
If the occasion arises to re-enable it:
```
sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target


```
Result:
```
Removed /etc/systemd/system/sleep.target.
Removed /etc/systemd/system/suspend.target.
Removed /etc/systemd/system/hibernate.target.
Removed /etc/systemd/system/hybrid-sleep.target.

```

---


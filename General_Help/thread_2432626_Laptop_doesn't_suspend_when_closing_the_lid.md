---
title: "Laptop doesn't suspend when closing the lid"
date: 2019-12-05
forum: General Help
---

### Post by paperos on 2019-12-05
Hello,
I have a fresh Ubuntu 18.04 LTS install on a brand new Lenovo IdeaPad 330 laptop. Everything works perfectly, except for one thing: when closing the lid, nothing happens. It isn't the problem with suspending itself (it works fine with pressing ALT button and clicking the power icon), what I discovered is that Ubuntu recognizes the laptop lid state always open. However, when I suspend it this way (ALT+click pwr icon), close the lid, then open, it wakes up automatically - no problem with the hardware I guess.

```
while true; do sleep 1; cat /proc/acpi/button/lid/LID0/state ; done
``` 

Running the script above, closing and opening the lid shows the state "Open" with every measurement, no matter if the lid is open or closed.
Tried to edit /etc/systemd/logind.conf, but it doesn't do anything, because the system thinks that lid is open all the time. 

I have no clue what to do now, I need some help :)
Thank you, 
Pat

---

### Post by gnusci on 2019-12-05
Can you post the output of:

$ uname -a
$ lsb_release -a

---

### Post by SeijiSensei on 2019-12-05
Have you checked the options in Power settings? What do you have as the setting for what to do when the lid is closed?

---

### Post by paperos on 2019-12-07
```
uname -a
Linux joanna-Lenovo-ideapad-330-15ICH 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


```

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic

```

There's no options in preferences for the lid, only for the power button. I read somewhere it was removed because of a bug that caused problems when connecting external monitor. However I installed the Tweak Tool and there is indeed an option to suspend when lid is closed and it's set to "on".

---

### Post by GhX6GZMB on 2019-12-07
Edit the contents of /etc/systemd/logind.conf
Suspend is normally not a big issue, Hibernate needs much more attention and setup.

---

### Post by SeijiSensei on 2019-12-07
> **paperos said:**
> 
There's no options in preferences for the lid, only for the power button.
Hmm. I use Kubuntu, and that option has been in System Settings for as long as I can remember. I just checked now, and it's still there in 19.10.

---

### Post by paperos on 2019-12-08
I edited /etc/systemd/logind.conf, but no luck. Ubuntu doesn't recognize the lid closed, so it has no effect.

---

### Post by gnusci on 2019-12-08
You need to upgrade to a newer Ubuntu. 19.10:

[http://releases.ubuntu.com/19.10/](http://releases.ubuntu.com/19.10/)

LTS, support older hardware, you need a newer kernel.

---


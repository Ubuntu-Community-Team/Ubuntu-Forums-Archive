---
title: "Unable to boot due to driver issue"
date: 2014-03-30
forum: General Help
---

### Post by nissim.lavy1 on 2014-03-30
Ubuntu 12.04 LTS

I've been having an issue booting up for a while. When I turn on my computer, I get this [screen]("http://i.imgur.com/M0kEGvr.jpg") and I cant really do anything beyond that. I've tried reinstalling Ubuntu and and that worked but after doing a restart, I get back to this screen and I can't boot up. I'm fairly certain that this is caused by a driver update I did.

I tried to install a driver update from a github repo that was recommended in a lot of askUbuntu posts. The driver in question is rtl8192ce, a Reatek wifi driver. I think that this is the cause because the output on that screenshot mentions that driver name a bunch of times.

Any ideas what I could to to fix this? I've already tried the reinstalling Ubuntu, recovering from an old version via the grub menu and nothing seemed to work.

I'm on ubuntu 12.04 LTS, Lenovo T530.

---

### Post by carl4926 on 2014-03-30
At the grub boot menu, select the advanced options and choose an older kernel. See if it will boot

---

### Post by nissim.lavy1 on 2014-03-30
At the GRUB menu, I can choose to use a previous version of linux. When I select that I only have 2 options, Ubuntu, with Linux 3.5.0-23-generic and the same thing in recovery mode. If I choose the recovery option, I can get to a terminal screen but after about a minute, the screen goes black and I would need to restart to do anything.

---

### Post by slooksterpsv on 2014-03-30
Go to the Recovery boot option, load it, get to the terminal and run:
sudo modprobe -r rtl8192ce

Then type exit and resume a normal boot.

---

### Post by nissim.lavy1 on 2014-03-30
I get a different error message now, [http://imgur.com/phNmuwt](http://imgur.com/phNmuwt) 
But then it goes back to the original error message

---

### Post by carl4926 on 2014-03-31
> **slooksterpsv said:**
> Go to the Recovery boot option, load it, get to the terminal and run:
sudo modprobe -r rtl8192ce

Then type exit and resume a normal boot.

Might it be

```
sudo modprobe -rv rtl8192ce
```

---

### Post by nissim.lavy1 on 2014-03-31
SOLVED! I blacklisted the module that was causing issues. But now I don't have any wireless internet since I blacklisted that module. Any way I can fix or reset that module so it wont cause me any issues?

---

### Post by carl4926 on 2014-03-31
Why were you messing with the git packages in the first place?

---

### Post by nissim.lavy1 on 2014-03-31
Not git packages, but my wireless module. I was trying to see if I can fix it because it was terrible before and barely worked. Realtek rtl8192ce on a Lenovo T530

---


---
title: "ubuntu 18.4.3 gets stuck on blank screensaver and trouble powering up"
date: 2019-12-12
forum: General Help
---

### Post by nocruoro on 2019-12-12
Like the title says i leave my computer on with screensaver and it's set to 60 minutes before blank. but it often gets stuck and its a notebook it takes several tries of angrily holding the power button and pressing until the blank screen stops and the acer powering up logo shows up.

how do i get rid of this stuck on **sleepsaver **problem.

I'm using ubuntu 18.4.3. 64-bit My computer had windows on it before but never had a problem like this before. (and it's not bad battery or faulty power cable)

---

### Post by nocruoro on 2019-12-13
bump

---

### Post by Impavidus on 2019-12-14
How stuck is it on that blank screen? Have you tried ctrl+alt+F1 through ctrl+alt+F7 to switch to the command line interface and back to the GUI? Have you tried SysRq+REISUB? When Ubuntu seems stuck, it's usually just the graphics that are stuck.

---

### Post by nocruoro on 2019-12-20
> **Impavidus said:**
> How stuck is it on that blank screen? Have you tried ctrl+alt+F1 through ctrl+alt+F7 to switch to the command line interface and back to the GUI? Have you tried SysRq+REISUB? When Ubuntu seems stuck, it's usually just the graphics that are stuck.

Yes and those tricks don't work on my laptop. It's just blank as of it has completely powered off. And sometimes it gets stuck and isn't turning on properly.

---

### Post by guiverc on 2019-12-20
Those are not 'tricks', but Sysrq keys speak directly to the kernel, so for the kernel to not respond implies to me either you haven't tried it (some laptops require a number of keys to achieve Sysrq, eg. holding down a FN key as well) OR your problem does **not** relate to screensaver but your machine has locked up & no longer functions (ie. kernel is dead & cannot be woken up, or hasn't been woken up yet).

I would then likely 'ssh' into your box (may require `openssh-server` to be installed and/or enabled) and monitor what occurs when it reaches that state hoping for messages or clues as to what is going on. If that didn't help, I'd explore `journalctl` (or systemd journal) for clues at the time of the 'sleep' event. 

I would expect sysrq keys to work though; and it's likely your keyboard requires a combination like some laptops I've used (where it's easier for me to use an external keyboard to enter the keystrokes...)

---

### Post by tea for one on 2019-12-20
Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a file:-

```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```

Then change the number in line 26 from 176 to 244 i.e. [B]kernel.sysrq = 244
[/B]
I found the solution at this site [https://digitalfortress.tech/debug/w...buntu-freezes/](https://digitalfortress.tech/debug/w...buntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by nocruoro on 2019-12-22
> **tea for one said:**
> Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a file:-

```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```

Then change the number in line 26 from 176 to 244 i.e. [B]kernel.sysrq = 244
[/B]
I found the solution at this site [https://digitalfortress.tech/debug/w...buntu-freezes/](https://digitalfortress.tech/debug/w...buntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

hasn't worked for me

---

### Post by tea for one on 2019-12-22
> **nocruoro said:**
> hasn't worked for me

That's surprising, a bit more info would be helpful.

Which part of this operation has not worked for you?

Did you successfully change the file?

Please post ```
/etc/sysctl.d/10-magic-sysrq.conf
```

Did you press and hold **Alt**?

Did you press **PrintScreen** and release?

Did you leave a two second gap between pressing each key **r e i s u b **?

---

### Post by nocruoro on 2019-12-22
> **tea for one said:**
> That's surprising, a bit more info would be helpful.

Which part of this operation has not worked for you?

Did you successfully change the file?

Please post ```
/etc/sysctl.d/10-magic-sysrq.conf
```

Did you press and hold **Alt**?

Did you press **PrintScreen** and release?

Did you leave a two second gap between pressing each key **r e i s u b **?

Yes i've resorted to simply powering off completely everytime before bed or leaving for long periods.

---


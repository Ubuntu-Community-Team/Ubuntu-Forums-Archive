---
title: "How do I check if a reboot is required after upgrading using apt-get?"
date: 2019-05-15
forum: General Help
---

### Post by janlz on 2019-05-15
I would like to know if it's possible to check whether a reboot is required or not after upgrading packages using [FONT=courier new]apt-get[/FONT]. Certain packages warn you about upgrading the system, like [FONT=courier new]intel-microcode[/FONT], which warns the following when upgrading:
```
intel-microcode: microcode will be updated at next boot
```

But there are packages that don't warn you. The kernel is one of them.

I've tried searching a way to know this on the Internet, but most websites check the presence of the [FONT=courier new]/var/run/reboot-required[/FONT] file. The file is created by the update manager but [FONT=courier new]apt-get[/FONT] **doesn't create it** (at least it doesn't on my system).

How do I check if a reboot is required after using [FONT=courier new]apt-get[/FONT]?
If it's relevant, I'm using Ubuntu MATE 18.04.2 LTS.

Thanks in advance.

---

### Post by Dennis N on 2019-05-15
Why not use Software Updater? When Software Updater utility finishes updating, if a restart is necessary to complete the update, it will pop up a message box informing you that the computer needs to restart to complete the updates. There are two options presented: Restart Now and Restart Later.

---

### Post by Rubi1200 on 2019-05-15
As far as I can tell there is no way to use apt or apt-get to provide the information you want.

Either use the method Dennis N suggests or perhaps this would work:

```
cat /var/run/reboot-required.pkgs
```

Output would be, just as an example, something like this (assuming there is something that requires a restart since the file is only created if the need exists):

```
linux-image-4.4.0-92-generic
```

Then, run:

```
sudo reboot
```

---

### Post by Bashing-om on 2019-05-15
janlz; Hello -

I am aware of a couple of means to see what the system thinks in respect to a required reboot.

When a reboot is required these files will exist:
[LIST]
[*]/var/run/reboot-required
[*]/var/run/reboot-required.pkgs
[*]/usr/lib/update-notifier/apt-check --human-readable
[*]
[/LIST]

[INDENT]hope this helps
[/INDENT]

---

### Post by Claus7 on 2019-05-16
Hello,

if I choose to logout then it informs me that some system updates won't be applied unless reboot takes place. Then I can choose cancel and reboot.

Regards!

---

### Post by oldrocker99 on 2019-05-16
Anything related to the kernel, like nVidia drivers, or a new kernel, do require a reboot. Otherwise, there's no need to do it, in my experience. There are a few programs that have to be in the startup-sequence, and, of course, it being Linux, there's no **need** to reboot unless you want to.

Few programs inform you that a reboot is needed. The examples above are when I personally reboot, and know a reboot is needed.

By the way, use **apt** instead of **apt-get**. Apt is, IMHO, superior to apt-get.

---

### Post by janlz on 2019-05-16
> **Dennis N said:**
> Why not use Software Updater? When Software  Updater utility finishes updating, if a restart is necessary to complete  the update, it will pop up a message box informing you that the  computer needs to restart to complete the updates. There are two options  presented: Restart Now and Restart Later.
Because the  software updater doesn't show updates that are not security updates as soon as they're available. I've sometimes checked if there are any updates available  using the software updater but it said there weren't. But if I checked  using [FONT=courier new]apt-get[/FONT], they were shown.

> **Rubi1200 said:**
> As far as I can tell there is no way to use apt or apt-get to provide the information you want.

Either use the method Dennis N suggests or perhaps this would work:

```
cat /var/run/reboot-required.pkgs
```

Output would be, just as an example, something like this (assuming there  is something that requires a restart since the file is only created if  the need exists):

```
linux-image-4.4.0-92-generic
```

Then, run:

```
sudo reboot
```

> **Bashing-om said:**
> janlz; Hello -

I am aware of a couple of means to see what the system thinks in respect to a required reboot.

When a reboot is required these files will exist:
[LIST]
[*]/var/run/reboot-required
[*]/var/run/reboot-required.pkgs
[*]/usr/lib/update-notifier/apt-check --human-readable
[/LIST]
[INDENT]hope this helps
[/INDENT]


These files are only created when the update manager tells me an update is available, because I configured it to show them immediately. If I update using [FONT=courier new]apt-get[/FONT] and run the software manager afterwards, it warns me a reboot is required even if I didn't update anything using it. But it doesn't always work.

> **Claus7 said:**
> Hello,

if I choose to logout then it informs me that some system updates won't  be applied unless reboot takes place. Then I can choose cancel and  reboot.

Regards!
I tried this on a virtual machine and I'm not told that if I log out. Are you using Ubuntu MATE?

> **oldrocker99 said:**
> Anything related to the kernel, like nVidia  drivers, or a new kernel, do require a reboot. Otherwise, there's no  need to do it, in my experience. There are a few programs that have to  be in the startup-sequence, and, of course, it being Linux, there's no **need** to reboot unless you want to.

Few programs inform you that a reboot is needed. The examples above are when I personally reboot, and know a reboot is needed.
Well, that's what I'm currently doing as well, if a package like systemd is upgraded, I reboot the computer. If it's a program like Firefox, then I just close any Firefox process I'm running. But it would be nice if I were warned when a reboot is required.

---

### Post by Claus7 on 2019-05-17
Hello,

> **janlz said:**
> 
I tried this on a virtual machine and I'm not told that if I log out. Are you using Ubuntu MATE?


I'm using flashback. I do not know if the difference in the gtk engine responds differently for these desktop sessions. Not aware how other sessions respond as well.

Regards!

---

### Post by janlz on 2019-05-17
> **Claus7 said:**
> 
I'm using flashback. I do not know if the difference in the gtk engine responds differently for these desktop sessions. Not aware how other sessions respond as well.


It looks like this is a GNOME feature that is not present in other flavors. I tested this on my laptop, which has Lubuntu 18.04 LTS installed, and nothing is shown when logging out either.

---

### Post by Claus7 on 2019-05-17
Hello,

in the old days, if reboot was about to take place, then I remember that the system explicitly informed about such a task and prompted you to close all programs for the changes to take effect...

xorg and kernel updates for sure require restart, as -more or less- already mentioned from *oldrocker99*. Not aware of how you will be able to verify it for sure though.

Good luck,
Regards!

---

### Post by TheFu on 2019-05-17
I check if /var/run/reboot-required exists.  Yes, then a reboot is needed.

Didn't look at any of the follow up questions.

---


---
title: "problem after instalation.."
date: 2007-06-27
forum: General Help
---

### Post by kirtikjr on 2007-06-27
i download ubuntu-7.04-desktop-i386 and i booted my system thru the cd..
it was very slow.. when i installed it, it does not start..i rebooted  2 or 3 times then it started..whats the problem and whats the default root password ??
(my system already had windows xp, rhel 4.0.. i formatted rhel 4.0 to install Ubuntu..)

---

### Post by MikeEvans on 2007-06-27
Need more info to troubleshoot the speed.  Whats your systems stats (CPU, RAM, VIDEO,...)?

There is no root password.  You can make one if you must but it's not recommended.  When you need to run a command as root use sudo.  For example, lets say you want to edit fstab. You would type the following into the terminal:
```
sudo gedit /etc/fstab
```
When it asks for a password type in your user password.

---

### Post by kirtikjr on 2007-06-27
my system stats: 256 mb ram, P4 2.4 GHz, intel 845 chipsets with no extra graphics cards..
please tell me why doesn't my system does boot into ubuntu now ?? just i had booted once, but it took a lot of time.. :(:(:(

---

### Post by logos34 on 2007-06-27
> **kirtikjr said:**
> my system stats: 256 mb ram, P4 2.4 GHz, intel 845 chipsets with no extra graphics cards..
please tell me why doesn't my system does boot into ubuntu now ?? just i had booted once, but it took a lot of time.. :(:(:(

You're running Ubuntu Feisty on the minimum recommended RAM.  This is likely part, if not all, of the problem.  Personally I would recommend you try Xubuntu--it's a lot smaller and lighter (Xfce desktop).

---

### Post by MikeEvans on 2007-06-27
logos34 is correct about your RAM but I don't think that would significantly slow down your boot time.  How long does it take to load when its successful?

Next, I assume you can at least get to the command prompt.  If not try starting in recovery mode which skips loading the graphical interface and drops you on the command prompt.  Once there you can check your logs for errors.  Here is an article that explains the logs and how to read them.
[http://www.ibm.com/developerworks/linux/library/l-roadmap5/]("http://www.ibm.com/developerworks/linux/library/l-roadmap5/")

To view your main system log that should have any boot or system errors:
```
nano /var/log/messages
```

To see errors related to X (graphical environment)
```
nano /var/log/Xorg.0.log
```

Also, it is strange that your system boots once but then not again.  Do you remember making any system changes when it loaded?  If not I would be concerned about the health of your hard drive.  Is it making any clicking noises when your system "hangs"?

---

### Post by RedSquirrel on 2007-06-27
> **kirtikjr said:**
> my system stats: 256 mb ram, P4 2.4 GHz, intel 845 chipsets with no extra graphics cards..
please tell me why doesn't my system does boot into ubuntu now ?? just i had booted once, but it took a lot of time.. :(:(:(

Intel Integrated graphics use part of your RAM for video, so I would recommend upgrading the RAM or trying Xubuntu.



> **MikeEvans said:**
> For example, lets say you want to edit fstab. You would type the following into the terminal:
```
sudo gedit /etc/fstab
```When it asks for a password type in your user password.

Remember to use **gksudo** for graphical applications. ;)

```
 gksudo gedit /etc/fstab
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MikeEvans on 2007-06-28
Good tip RedSquirrel, I wasn't aware of gksudo until just now  ;)

---


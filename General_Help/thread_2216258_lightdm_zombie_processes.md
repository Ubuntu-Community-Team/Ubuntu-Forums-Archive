---
title: "lightdm zombie processes"
date: 2014-04-10
forum: General Help
---

### Post by KenF on 2014-04-10
On my 12.04 installs, I accumulate a lot of defunct (zombie) processes.  I seem to accumulate one every time I switch users.  It may be disconnected from this, but I notice serious degraded performance (Xorg issues, large CPU usage) after more than 100 of these accumulate.  I rebooted this morning and already have 6.  [Running Unity 2d]:

[INDENT]me@mymachine:/media/ken/diskstation/work/Programs$ ps aux | grep Z

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root      4192  0.0  0.0      0     0 ?        Z    13:09   0:00 [lightdm] <defunct>
root      5613  0.0  0.0      0     0 ?        Z    15:15   0:00 [lightdm] <defunct>
root      5665  0.0  0.0      0     0 ?        Z    15:15   0:00 [lightdm] <defunct>
root      7352  0.0  0.0      0     0 ?        Z    17:35   0:00 [lightdm] <defunct>
root      7757  0.0  0.0      0     0 ?        Z    18:56   0:00 [lightdm] <defunct>
root      7808  0.0  0.0      0     0 ?        Z    18:56   0:00 [lightdm] <defunct>
[/INDENT]

---

### Post by bapoumba on 2014-04-11
```
bapoumba_lxde@SonyBlue:~$ ps aux | grep Z
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
bapoumb+  2379  0.0  0.0      0     0 ?        Z    avril11   0:00 [sd_cicero] <defunct>
bapoumb+  4445  0.0  0.0   6160   836 pts/2    S+   00:18   0:00 grep --color=auto Z

bapoumba_lxde@SonyBlue:~$ ps aux | grep Z
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
bapoumb+  2379  0.0  0.0      0     0 ?        Z    avril11   0:00 [sd_cicero] <defunct>
bapoumb+  5512  0.0  0.0   6156   836 pts/2    D+   00:24   0:00 grep --color=auto Z

bapoumba_lxde@SonyBlue:~$ ps aux | grep Z
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
bapoumb+  2379  0.0  0.0      0     0 ?        Z    avril11   0:00 [sd_cicero] <defunct>
bapoumb+  5994  0.0  0.0   6160   836 pts/2    S+   00:29   0:00 grep --color=auto Z


```

Fist one : one user only. Second one, after switching user, then going back to the first user, not logging out of the second one. Third one after logging out of the second user.

---

### Post by KenF on 2014-04-13
Are you using Unity or LXDE?

What is your Display Manager ... is it lightdm?  I guess that gdm and lxdm are possibilities that wouldn't encounter this?

---

### Post by bapoumba on 2014-04-13
> **KenF said:**
> Are you using Unity or LXDE?

What is your Display Manager ... is it lightdm?  I guess that gdm and lxdm are possibilities that wouldn't encounter this?

Good point, LXDE, and I missed the comment about Unity 2D in your first post. And yes, lightdm. I cannot try with GDM/Unity, although I have ubuntu-desktop installed, my laptop does not bare with unity any more.

---

### Post by KenF on 2014-04-13
Mine is a default Unity 2D install and uses lightdm.   If you are using lightdm ... my issue must be the combination of Unity 2D and lightdm.   As an update:

> ps aux | grep Z | grep lightdm
root      1457  0.0  0.0      0     0 ?        Z    Apr10   0:00 [lightdm] <defunct>
root      1808  0.0  0.0      0     0 ?        Z    Apr10   0:00 [lightdm] <defunct>
root      1809  0.0  0.0      0     0 ?        Z    Apr10   0:00 [lightdm] <defunct>
root      5280  0.0  0.0      0     0 ?        Z    Apr11   0:00 [lightdm] <defunct>
root      6981  0.0  0.0      0     0 ?        Z    Apr11   0:00 [lightdm] <defunct>
root      7032  0.0  0.0      0     0 ?        Z    Apr11   0:00 [lightdm] <defunct>
root      7898  0.0  0.0      0     0 ?        Z    Apr11   0:00 [lightdm] <defunct>
root      8838  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root      8889  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root      9580  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root     10245  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root     10297  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root     10812  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root     11799  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root     11849  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root     16844  0.0  0.0      0     0 ?        Z    Apr12   0:00 [lightdm] <defunct>
root     17496  0.0  0.0      0     0 ?        Z    07:12   0:00 [lightdm] <defunct>
root     17549  0.0  0.0      0     0 ?        Z    07:12   0:00 [lightdm] <defunct>


---

### Post by bapoumba on 2014-04-14
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/993573](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/993573)
[https://bugs.launchpad.net/lightdm/+bug/990661](https://bugs.launchpad.net/lightdm/+bug/990661)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=675351](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=675351)

Which lightdm package are you using ?

---

### Post by KenF on 2014-04-14
I'm running lightdm 1.2.3 on an up-to-date 32bit 12.04 using Unity 2D. 

Those bugs sound exactly like my issue.  From one report it looks like it was fixed in 1.3.3.  I guess the fix hasn't been backported to 12.04 LTS ???   I'm not moving to 14.04 Unity since there's no Unity 2D support and my video card just can't do that.  Perhaps the best solution is to go to Xubuntu 14.04 once it gets settled down.  Advice?

---

### Post by bapoumba on 2014-04-15
> **KenF said:**
> I'm running lightdm 1.2.3 on an up-to-date 32bit 12.04 using Unity 2D. 

Those bugs sound exactly like my issue.  From one report it looks like it was fixed in 1.3.3.  I guess the fix hasn't been backported to 12.04 LTS ???   I'm not moving to 14.04 Unity since there's no Unity 2D support and my video card just can't do that.  Perhaps the best solution is to go to Xubuntu 14.04 once it gets settled down.  Advice?

Well, I choose lubuntu because i had tried xubuntu some time ago and wanted to test this baby. I like both, could find my way easily with both, so it is really up to you. My laptop is on the lower end of nowadays configs and cannot run unity any more. It does run, but lags, swaps a lot and many applications just hang and grey out before they get active again. The HD gets accessed a lot due to swapping and the computer heats up, making fans working constantly. None of that with lubuntu.

May be you could try both from live sessions and decide which one works best or which environment has your preference.

---


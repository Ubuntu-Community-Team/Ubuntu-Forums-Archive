---
title: "Halted  &quot;waiting for cron&quot;"
date: 2020-08-13
forum: General Help
---

### Post by kholusoft on 2020-08-13
I am facing the similar issue on my NUC8i3BEH. I have installed fresh Kubuntu 20.04
Everything is fine except the shutdown time 
It hangs at 
```
systemd-shutdown[1] waiting for process : crond
```

---

### Post by kholusoft on 2020-08-29
Sorry for bumping. Can anyone help. I am desperate.

---

### Post by QIII on 2020-08-30
Moved to its own thread from [here.]("https://ubuntuforums.org/showthread.php?t=2442125")

Please do not hijack the posts of other users.  While your symptoms may seem similar, the root cause may be entirely different.  When two (or more) different users start asking for support in the same thread, it quickly becomes confusing for both the user and those trying to help.  We believe that everyone deserves individual support because the underlying problem may be different, so we do not close similar threads started by different users as some sites do.

---

### Post by SeijiSensei on 2020-08-31
Before shutting down, open a terminal and type
```
sudo systemctl stop cron
```
Does that return an error?  You can check that cron is stopped with
```
ps ax | grep cron
```
That should return
```
grep --color=auto cron
```
which is just repeating back the command after the "pipe," represented by the vertical bar.  If cron is still running you should also see the line
```
/usr/sbin/cron -f
```
If cron has stopped, retry the shutdown command.

In my experience cron may not be the problem (likely it is not), but that whatever comes next in the shutdown sequence is hanging. 

This is on Kubuntu 20.04.

---


---
title: "Failing to sleep after inactivity - power manager error?"
date: 2015-04-05
forum: General Help
---

### Post by michael.kalisz on 2015-04-05
Hi,

XUbuntu 14.10

I'm basically having the same problem as this question:

[http://askubuntu.com/questions/590488/xubuntu-14-10-failing-to-sleep-after-inactivity-power-manager-error](http://askubuntu.com/questions/590488/xubuntu-14-10-failing-to-sleep-after-inactivity-power-manager-error)

Anyone managed to get the power manager to suspend the machine?

I want my machine to suspend after a certain time..but keep getting the

```
Power Manager Error  
GDBus.Error:org.freedesktop.DBus.Error.NoReply:
Did not receive a reply. Possible causes include: the
remote application did not send a reply, the message
bus security policy blocked the reply, the reply
timeout expired, or the network connection was 
broken.
```

Any hints how to solve this?

Thanks in advance

Michael

---

### Post by ajgreeny on 2015-04-05
Can you suspend from the logout dialogue  box or does that also error out?

---

### Post by michael.kalisz on 2015-04-05
> **ajgreeny said:**
> Can you suspend from the logout dialogue  box or does that also error out?

yes,

but running:

$ pm-suspend
This utility may only be run by the root user 

But this command suspends the system just fine:

$ dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend

$ xfce4-power-manager --dump 
---------------------------------------------------
       Xfce power manager version 1.4.1
With policykit support
With network manager support
---------------------------------------------------
**Can suspend: True**
Can hibernate: False
**Authorized to suspend: True**
Authorized to hibernate: False
Authorized to shutdown: True
Has battery: False
Has brightness panel: True
Has power button: True
Has hibernate button: True
Has sleep button: True
Has LID: False

So I guess It's an auth or policykit issue...

This is the message that meets me when I login after a failed suspend:

[IMG]http://s27.postimg.org/l24boyvqp/Screenshot_2015_04_05_15_20_38.png[/IMG]

---


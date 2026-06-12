---
title: "Help!! Can't get rid of vmnet1"
date: 2006-12-19
forum: General Help
---

### Post by hanzomon4 on 2006-12-19
Alright, I started getting this error after installing vmware-server:```
Dec 19 15:01:43 localhost kernel: [17180814.428000] unregister_netdevice: waiting for vmnet1 to become free. Usage count = 1
``` This just keeps repeating and nothing on my desktop works, not even rebooting. I have to cut the power to get it back working again......

Anyway, I ran**_ vmware-uninstall-mui.pl_** to uninstall vmware-server, it did but I'm still getting this error. So what can I do about this, I'll take any suggestions

---

### Post by amd-64 on 2006-12-19
If vmware was not uninstalled cleanly, this may help

```
sudo /etc/init.d/vmware stop
sudo rmmod vmnet vmmon
sudo /etc/init.d/networking restart
```

Consider removing any vmware files manually (use with care!)
rm -r /etc/vmware
find and remove the vm modules vmmon and vmnet, mine are under /lib/modules/'uname -r'/misc/

---

### Post by hanzomon4 on 2006-12-20
> **amd-64 said:**
> If vmware was not uninstalled cleanly, this may help

```
sudo /etc/init.d/vmware stop
sudo rmmod vmnet vmmon
sudo /etc/init.d/networking restart
```

Consider removing any vmware files manually (use with care!)
rm -r /etc/vmware
find and remove the vm modules vmmon and vmnet, mine are under /lib/modules/'uname -r'/misc/

Thanks, :fingers crossed: I hope this works

---

### Post by hanzomon4 on 2006-12-21
I figured it out it wasn't really vmnet that was causing the problem....  Once I got rid of vmnet the problem started happaning with eth0. I checked out the syslog and found that my computer would suspend right before the error message started, I also noticed that after the computer "suspended" It would disable things related to eth0.
[LIST]
[*][COLOR="Red"]**Suspend message**[/COLOR]
[*][COLOR="Green"]**Disabling eth0 message**[/COLOR]
[*][COLOR="Blue"]**Error message**[/COLOR]  
[/LIST]



 ```
[B][COLOR="Red"]Dec 19 00:57:31 localhost gnome-power-manager: (********) Suspending computer b
ecause the system state is idle[/COLOR][/B]
Dec 19 00:57:32 localhost NetworkManager: <information>^IGoing to sleep. 
[B][COLOR="Green"]Dec 19 00:57:34 localhost kernel: [17283759.784000] remove_proc_entry: 209/eth0 
busy, count=14
Dec 19 00:57:34 localhost kernel: [17283759.784000] bridge-eth0: disabling the b
ridge
Dec 19 00:57:35 localhost kernel: [17283759.812000] bridge-eth0: down
Dec 19 00:57:36 localhost NetworkManager: <debug info>^I[1166511456.677815] nm_h
al_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/n
et_00_11_11_e2_17_dd').[/COLOR][/B]
[B][COLOR="Blue"]Dec 19 00:57:46 localhost kernel: [17283771.644000] unregister_netdevice: waitin
g for eth0 to become free. Usage count = 1[/COLOR][/B]
Dec 19 00:57:56 localhost gnome-power-manager: (*******) Resuming computer
Dec 19 00:57:57 localhost NetworkManager: <information>^IWaking up from sleep. 
Dec 19 00:57:57 localhost kernel: [17283781.884000] unregister_netdevice: waitin
g for eth0 to become free. Usage count = 1

```

I changed the power-management settings to stop it from suspending and that fixed the problem.

---

### Post by Tiptup300 on 2006-12-23
How did you fix it, its giving huge problems and I want rid of it

---

### Post by towsonu2003 on 2006-12-23
i'm guessing;
applications - system tools - configuration editor - 
apps - gnome-power-manager - uncheck 'can hibernate' 'can sleep'

ps. this is a gnome-power-manager bug i think, you migh want to report it if not already reported at
[https://bugs.launchpad.net/distros/ubuntu/+source/gnome-power-manager/+filebug](https://bugs.launchpad.net/distros/ubuntu/+source/gnome-power-manager/+filebug)

---

### Post by Deathmoon on 2006-12-23
> **towsonu2003 said:**
> i'm guessing;
applications - system tools - configuration editor - 
apps - gnome-power-manager - uncheck 'can hibernate' 'can sleep'

ps. this is a gnome-power-manager bug i think, you migh want to report it if not already reported at
[https://bugs.launchpad.net/distros/ubuntu/+source/gnome-power-manager/+filebug](https://bugs.launchpad.net/distros/ubuntu/+source/gnome-power-manager/+filebug)

Awesome!  Thank you, this solved the problem.

---


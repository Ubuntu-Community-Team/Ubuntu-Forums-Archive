---
title: "Where is my shutdown log file?"
date: 2008-03-21
forum: General Help
---

### Post by Bruce M. on 2008-03-21
Hi Folks,

Every time I "shut down" I see Network Manager type errors, but can't find a file that shows them.

Unless this is it, in /var/log/syslog.0

```

Mar 21 08:24:27 bruloo NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) failure scheduled... 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 21 08:24:27 bruloo NetworkManager: <debug> [1206098667.306093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a4a7e90e_6e66_4a3b_a3be_8c5259b7f32b'). 
Mar 21 08:24:27 bruloo NetworkManager: <debug> [1206098667.338579] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD400EB_00CPF0_WD_WCAATE196342'). 
Mar 21 08:24:27 bruloo NetworkManager: <debug> [1206098667.444591] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_28677b39_1f49_4d6c_a3b9_5b4002f6f66e'). 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) failed. 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Deactivating device eth0. 
Mar 21 08:24:27 bruloo NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Mar 21 08:24:27 bruloo NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Will activate connection 'eth0'. 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Device eth0 activation scheduled... 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) started... 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar 21 08:24:27 bruloo NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) failure scheduled... 
Mar 21 08:24:27 bruloo NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 

```

that repeats over and over.

Any idea what to look for and how to fix it?
Bruce

---

### Post by Bruce M. on 2008-03-29
Bump...
Also I've noticed this:

When I "Shutdown" for the night one of the last things I see along with the "Failed" things regarding Netwrok Manager is this message:

> Make sure the message bus daemon is running.

Any ideas as to what this is and or how to activate it?

Thanks
Bruce

---

### Post by mali2297 on 2008-03-29
> **Bruce M. said:**
> Bump...
Also I've noticed this:

When I "Shutdown" for the night one of the last things I see along with the "Failed" things regarding Netwrok Manager is this message:



Any ideas as to what this is and or how to activate it?

Thanks
Bruce

That refers to [D-Bus]("http://www.freedesktop.org/wiki/Software/dbus"), it should launch automatically at startup.

To see that it is running, you can use the following terminal command:
```

ps -e | grep dbus

```

Do you experience any problems with the network connection, or are you just annoyed by the error messages?

---

### Post by Bruce M. on 2008-03-29
> **mali2297 said:**
> That refers to [D-Bus]("http://www.freedesktop.org/wiki/Software/dbus"), it should launch automatically at startup.

To see that it is running, you can use the following terminal command:
```

ps -e | grep dbus

```

Thanks for the link, will read it later today.
I see:

```
bruloo@bruloo:~$ ps -e | grep dbus
 4494 ?        00:00:00 dbus-daemon
 4538 ?        00:00:00 dbus-daemon
 5522 ?        00:00:00 dbus-launch
 5523 ?        00:00:00 dbus-daemon
bruloo@bruloo:~$ 
```

No idea what that means.

> **mali2297 said:**
> Do you experience any problems with the network connection, or are you just annoyed by the error messages?

No no problems, everything works just fine. There is a "Wired Network Connection" Icon in the upper panel on the right.  If I disable that, I can't get to the net, therefore it's disabling my eth0 card. It always starts "open" and I leave it that way.

If someone told me the messages are nothing to worry about, and explained why, I would simply ignore them.

However I'm of the mindset that "Failed" or "WARN" type messages need attention of some type.

Thanks
Bruce

---

### Post by mali2297 on 2008-03-29
> **Bruce M. said:**
> 
```
bruloo@bruloo:~$ ps -e | grep dbus
 4494 ?        00:00:00 dbus-daemon
 4538 ?        00:00:00 dbus-daemon
 5522 ?        00:00:00 dbus-launch
 5523 ?        00:00:00 dbus-daemon
bruloo@bruloo:~$ 
```

No idea what that means.

It means that you have D-Bus running (several instances).

> 
No no problems, everything works just fine. There is a "Wired Network Connection" Icon in the upper panel on the right.  If I disable that, I can't get to the net, therefore it's disabling my eth0 card. It always starts "open" and I leave it that way.

If someone told me the messages are nothing to worry about, and explained why, I would simply ignore them.

However I'm of the mindset that "Failed" or "WARN" type messages need attention of some type.


There is a difference between *warnings* and *errors*, one can most often ignore the former. If something was marked as Failed at startup, then it might be worth looking into. But when shutting down... nah, I don't know. :-|

---

### Post by Bruce M. on 2008-03-29
> **mali2297 said:**
> It means that you have D-Bus running (several instances).

Several, I see at least 3 the same, is this good, bad or ??

> **mali2297 said:**
> There is a difference between *warnings* and *errors*, one can most often ignore the former. If something was marked as Failed at startup, then it might be worth looking into. But when shutting down... nah, I don't know. :-|

Well, it's not doing any harm, and things are working, so I'm not going to panic.  :)

---

### Post by mali2297 on 2008-03-29
> **Bruce M. said:**
> Several, I see at least 3 the same, is this good, bad or??

I think it's normal. I also have several such processes. Among the apps that require dbus are Thunar and NetworkManager. It might be that each of these creates its own instance of dbus.

---

### Post by Bruce M. on 2008-03-29
> **mali2297 said:**
> I think it's normal. I also have several such processes. Among the apps that require dbus are Thunar and NetworkManager. It might be that each of these creates its own instance of dbus.

makes sense then, I'm using both.  :)

---


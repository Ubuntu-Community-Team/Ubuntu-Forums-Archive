---
title: "woke up, pc had shut down, help!!!!"
date: 2008-06-21
forum: General Help
---

### Post by Majin_Buu on 2008-06-21
Good morning!

I just awoke a couple of minutes ago, and to my suprise my pc had shut it self down.

If this was on windows I wouldn't have been suprised, but this time it's not.

[SIZE="4"]EDIT: I just realised my pc was still running (I could hear my cpu fan etc) but it couldn't get a signal from the gpu (my screen shows the gpu display on the monitor if its trying to find a signal), the screen was black, no response from the mouse or keyboard, numlock didn't work either, a freeze maybe?[/SIZE]

**How do I start a debugg in order to locate the mysterious error that caused my pc to shut it self down?**

Thank You

---

### Post by ramjet_1953 on 2008-06-21
Try this BEFORE doing a power re-set.

It will safely shut down your system.

Alt+SysReq+r

Alt+SysReq+s

Alt+SysReq+e

Alt+SysReq+i

Alt+SysReq+u

Alt+SysReq+b

Hopefully, this will do the trick.

Do not miss out any steps and allow a few seconds between commands.

You will not see anything happen, until you execute the last command.

Regards,
Roger :cool:

---

### Post by Majin_Buu on 2008-06-21
> **ramjet_1953 said:**
> Try this BEFORE doing a power re-set.

It will safely shut down your system.

Alt+SysReq+r

Alt+SysReq+s

Alt+SysReq+e

Alt+SysReq+i

Alt+SysReq+u

Alt+SysReq+b

Hopefully, this will do the trick.

Do not miss out any steps and allow a few seconds between commands.

You will not see anything happen, until you execute the last command.

Regards,
Roger :cool:

Hi Roger! Thanks for for quick reply. But how will this show me any error log? 

When the freeze (i think) occurred there was just a black screen (no signal) so theres nothing to type in either, so I had to manually reboot by pressing the power button my chassi.

The reason i'm asking what those commands are for, is because im currently backing up a few vital files to my external hdds.

Thanks!

---

### Post by ramjet_1953 on 2008-06-21
Hi, Majin_Buu!

No, the above procedure will only safely shut down your system.

The key sequence that I gave you does the following:

[COLOR="Blue"]Alt+SysReq+r     Puts keyboard into raw mode

Alt+SysReq+s     Syncs the disk

Alt+SysReq+e     Terminates all processes

Alt+SysReq+i     Kills all processes

Alt+SysReq+u     Remounts all file systems as read-only

Alt+SysReq+b     Re-boots the system[/COLOR]

If you want to check error logs, here is a good link that explains all:

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Regards,
Roger :cool:

---

### Post by Unix-Advocate on 2008-06-21
I would recommend doing a soft reboot, ( holding down the power switch for ten seconds).

---

### Post by ramjet_1953 on 2008-06-21
Hi, Unix-Advocate:

Your suggestion is an ABSOLUTE LAST Resort.

This method can cause problems with data corruption on your Hard Drive.

It is NOT soft, by any stretch of the imigination.

If you read the explanation that I gave for the manual key sequence, you will see that it SAFELY re-boots your system, without fsck having to recover data.

Regards,
Roger :cool:

---

### Post by Unix-Advocate on 2008-06-22
> **ramjet_1953 said:**
> Hi, Unix-Advocate:

Your suggestion is an ABSOLUTE LAST Resort.

This method can cause problems with data corruption on your Hard Drive.

It is NOT soft, by any stretch of the imigination.

If you read the explanation that I gave for the manual key sequence, you will see that it SAFELY re-boots your system, without fsck having to recover data.

Regards,
Roger :cool:



Thanks for the tip Roger.

You might also want to try hooking the monitor up to your on board video card visa via the VGA cable as  trouble shooting or even ctrl+alt+delete.

I would appreciate it If once you found the error message in the logs you could please post the error message in question here on the forums, and ask a moderator to sticky this thread.

---

### Post by Majin_Buu on 2008-06-22
Duplicate message

---

### Post by Majin_Buu on 2008-06-22
I really hope someone can help me, maybe you roger?

Today when I woke up, the same thing, my computer went "black" screen after 8 hours (when I was sleepin) it wont react to my keyboard noir mouse input, i'm forced to reboot.

I read the link you showed me roger concerning those error logs, I printed out only the time where it died and when I woke up, there's not point printing everything.

_/var/log/auth.log_

```
Jun 22 11:09:01 skynet CRON[4106]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 22 11:09:01 skynet CRON[4106]: pam_unix(cron:session): session closed for user root
Jun 22 11:17:01 skynet CRON[4230]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 22 11:17:01 skynet CRON[4230]: pam_unix(cron:session): session closed for user root
Jun 22 11:39:01 skynet CRON[4543]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 22 11:39:02 skynet CRON[4543]: pam_unix(cron:session): session closed for user root
Jun 22 12:51:59 skynet kdm: :0[5333]: pam_unix(kdm:session): session opened for user greenfish by (uid=0)
```

_/var/log/daemon.log_

```
Jun 20 10:07:22 skynet dhclient: DHCPREQUEST of <null address> on eth0 to 10.125.3.11 port 67
Jun 20 10:07:22 skynet dhclient: DHCPACK of 83.254.181.216 from 10.125.3.11
Jun 20 10:07:22 skynet NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0
Jun 20 10:07:22 skynet dhclient: bound to 83.254.181.216 -- renewal in 991 seconds.
Jun 20 10:23:53 skynet dhclient: DHCPREQUEST of <null address> on eth0 to 10.125.3.11 port 67
Jun 20 10:23:54 skynet dhclient: DHCPACK of 83.254.181.216 from 10.125.3.11
Jun 20 10:23:54 skynet NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0
Jun 20 10:23:54 skynet dhclient: bound to 83.254.181.216 -- renewal in 9959 seconds.
[SIZE="4"][B]Jun 20 12:48:25 skynet kdm[5024]: X server terminated: [0, 0, 0]
Jun 20 12:48:25 skynet kdm[5024]: X server for display :0 terminated unexpectedly[/B][/SIZE]
Jun 20 12:48:25 skynet kdm[5024]: StartServerSucces
Jun 20 12:48:47 skynet NetworkManager: <info>  Updating allowed wireless network lists.
Jun 20 12:48:47 skynet NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks.
```

_/var/log/debug_

```
Jun 20 09:44:22 skynet audio[5416]: audio.conf: Key file does not have key 'Enable'
Jun 20 09:44:22 skynet audio[5416]: audio.conf: Key file does not have key 'Disable'
Jun 20 09:44:22 skynet audio[5416]: add_service_record: got record id 0x10000
Jun 20 09:44:22 skynet audio[5416]: audio.conf: Key file does not have key 'Disable'
Jun 20 09:44:22 skynet audio[5416]: audio.conf: Key file does not have group 'A2DP'
Jun 20 09:44:22 skynet last message repeated 3 times
Jun 20 09:44:22 skynet audio[5416]: SEP 0x806d4e8 registered: type:0 codec:0 seid:1
Jun 20 09:44:22 skynet audio[5416]: add_service_record: got record id 0x10001
Jun 20 09:44:22 skynet audio[5416]: add_service_record: got record id 0x10002
Jun 20 09:44:22 skynet audio[5416]: add_service_record: got record id 0x10003
Jun 20 09:44:40 skynet kernel: [   54.886915] eth0: no IPv6 routers present
**[SIZE="4"]Jun 20 13:51:50 skynet NetworkManager: <debug> [1213962710.349583] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_AirPlus_G').[[/SIZE]**
```

WOW notice the HUGE gap? 09:44 - 13:51

/var/log/kern.log

```
[B][SIZE="4"]Jun 22 03:04:23 skynet kernel: [ 9428.138246] usb 6-4: USB disconnect, address 4
Jun 22 12:51:41 skynet kernel: Inspecting /boot/System.map-2.6.24-19-generic[/SIZE][/B]
Jun 22 12:51:41 skynet kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jun 22 12:51:41 skynet kernel: Symbols match kernel version 2.6.24.
Jun 22 12:51:41 skynet kernel: Loaded 36486 symbols from 99 modules.
Jun 22 12:51:41 skynet kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 22 12:51:41 skynet kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 22 12:51:41 skynet kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jun 22 12:51:41 skynet kernel: [    0.000000] BIOS-provided physical RAM map:
```

Again notice the time gap 03:04 - 12:51 !!!!!

NOTE: Im not posting the entire log since it's HUGE!

_/var/log/messages_

```
Jun 22 03:04:23 skynet kernel: [ 9428.138246] usb 6-4: USB disconnect, address 4
Jun 22 03:29:22 skynet -- MARK --
Jun 22 03:49:22 skynet -- MARK --
Jun 22 04:09:22 skynet -- MARK --
Jun 22 04:29:22 skynet -- MARK --
Jun 22 04:49:22 skynet -- MARK --
Jun 22 05:09:22 skynet -- MARK --
Jun 22 05:29:22 skynet -- MARK --
Jun 22 05:49:22 skynet -- MARK --
Jun 22 06:09:22 skynet -- MARK --
Jun 22 06:29:22 skynet -- MARK --
Jun 22 06:49:22 skynet -- MARK --
Jun 22 07:09:22 skynet -- MARK --
Jun 22 07:29:22 skynet -- MARK --
Jun 22 07:37:48 skynet syslogd 1.5.0#1ubuntu1: restart.
Jun 22 07:49:22 skynet -- MARK --
Jun 22 08:09:22 skynet -- MARK --
Jun 22 08:29:22 skynet -- MARK --
Jun 22 08:49:22 skynet -- MARK --
Jun 22 09:09:22 skynet -- MARK --
Jun 22 09:29:22 skynet -- MARK --
Jun 22 09:49:22 skynet -- MARK --
Jun 22 10:09:22 skynet -- MARK --
Jun 22 10:29:22 skynet -- MARK --
Jun 22 10:49:22 skynet -- MARK --
Jun 22 11:09:22 skynet -- MARK --
Jun 22 11:29:22 skynet -- MARK --
Jun 22 12:51:41 skynet syslogd 1.5.0#1ubuntu1: restart.
Jun 22 12:51:41 skynet kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jun 22 12:51:41 skynet kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jun 22 12:51:41 skynet kernel: Symbols match kernel version 2.6.24.
Jun 22 12:51:41 skynet kernel: Loaded 36486 symbols from 99 modules.
Jun 22 12:51:41 skynet kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 22 12:51:41 skynet kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 22 12:51:41 skynet kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jun 22 12:51:41 skynet kernel: [    0.000000] BIOS-provided physical RAM map:
```

Hmm that's weird.. by the looks of things the computer is still running?

Anyone have any ideas at all?

---

### Post by Majin_Buu on 2008-06-23
*bump* :popcorn:

---


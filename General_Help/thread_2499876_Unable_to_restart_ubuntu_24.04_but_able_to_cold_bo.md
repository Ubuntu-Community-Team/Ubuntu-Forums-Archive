---
title: "Unable to restart ubuntu 24.04 but able to cold boot"
date: 2024-08-13
forum: General Help
---

### Post by ubuuser3482 on 2024-08-13
I recently installed Ubuntu 24.04 on a HP Elite Desk. I have run into a  problem where I am unable to restart Ubuntu but I have no problems  shutting it down or cold booting it from shutdown.

_**Context about my setup:**_
HP Elite Desk with an HDMI connection to a television running Ubuntu 24.04

_**Context about occurrence of the problem:**_
The  problem is whenever I try to restart using multiple different scenarios  my computer never fully restarts and I end up in a situation where the  computer is started but my television says there's no HDMI signal. Each  time this happens I power the machine off holding the power button and  then power back on and everything starts up fine.

All of the following scenarios have failed to restart for me:

[LIST]
[*]    after installation when it prompts you to remove the USB installation media and hit enter
[*]    after running Software Updater and click restart now
[*]    after clicking the restart button from the top right corner of the desktop (clicking Power off work fine)
[*]    after entering ```
sudo shutdown -r
``` in terminal
[/LIST]

[U][B]Diagnosis so far:

[/B][/U]I think on restart the X server is failing to start and I end up with my computer turned on but no HDMI signal out to the tv.

I am basing this on the following logs.

From ```
/var/log/syslog.log
``` I see the following:

```

2024-08-13T10:49:07.998071-06:00 /usr/libexec/gdm-x-session[1217]: (EE) no screens found(EE)
2024-08-13T10:49:07.998173-06:00 /usr/libexec/gdm-x-session[1217]: (EE) Please also check the  log file at "/var/log/Xorg.0.log" for additional information.
2024-08-13T10:49:07.998193-06:00 /usr/libexec/gdm-x-session[1217]: (EE)
2024-08-13T10:49:07.998467-06:00 /usr/libexec/gdm-x-session[1217]: (EE) Server terminated with  error (1). Closing log file.
2024-08-13T10:49:07.999551-06:00 /usr/libexec/gdm-x-session[1215]: Unable to run X server
2024-08-13T10:49:08.001786-06:00 gdm3: Gdm: GdmDisplay: Session never registered, failing

```

From  ```
/var/log/Xorg.0.log
``` I see it try to match multiple  settings to autoconfigured driver but none seem to match. I also see  entries in the log like
```

[ 17.845] (EE) open /dev/dri/card0: No such file or directory

```
but don't see any other cards it tries which is also curious cause when my system is running I see the following:
```

$ ls -al /dev/dri
total 0
drwxr-xr-x 3 root root 100 Aug 13 11:01 .
drwxr-xr-x 20 root root 4300 Aug 13 13:14 ..
drwxr-xr-x 2 root root 80 Aug 13 11:01 by-path
crw-rw----+ 1 root video 226, 1 Aug 13 11:01 card1
crw-rw----+ 1 root render 226, 128 Aug 13 11:01 renderD128

```
and
```

$ ls -al /dev/dri/by-path/
total 0
drwxr-xr-x 2 root root  80 Aug 13 11:01 .
drwxr-xr-x 3 root root 100 Aug 13 11:01 ..
lrwxrwxrwx 1 root root   8 Aug 13 11:01 pci-0000:00:02.0-card -> ../card1
lrwxrwxrwx 1 root root  13 Aug 13 11:01 pci-0000:00:02.0-render -> ../renderD128

```

Does it look like the X server failing to start would cause this problem?  If so, why would it be a problem on restarts but not cold boots?  Any help would be appreciated.

---

### Post by ubuuser3482 on 2024-08-13
One other thing I want to mention I tried troubleshooting.  I tried cold booting with my tv off and it cold boots fine in that scenario as well.

---

### Post by grahammechanical on 2024-08-13
> I think on restart the X server is failing to start and I end up with my computer turned on but no HDMI signal out to the tv.

Ubuntu 24.04 LTS usually defaults to using the Wayland windowing system and not the X-Server. Have you chosen to switch to using the X-Server?

Regards

---

### Post by oldfred on 2024-08-13
When installing grub uses efibootmgr to make "ubuntu" the first & default boot entry.
With HP it often works once & then HP resets boot to Windows.

Look in UEFI settings(not UEFI boot menu) and change boot order there.

Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)
HP Pavilion Plus 14  UEFI boot order for Ubuntu with Windows 11
[https://askubuntu.com/questions/1464469/windows-11-dual-boot-with-ubuntu-does-not-show-boot-menu/1465075#1465075](https://askubuntu.com/questions/1464469/windows-11-dual-boot-with-ubuntu-does-not-show-boot-menu/1465075#1465075)

---

### Post by ubuuser3482 on 2024-08-13
> **grahammechanical said:**
> Ubuntu 24.04 LTS usually defaults to using the Wayland windowing system and not the X-Server. Have you chosen to switch to using the X-Server?

Regards

No customization.  Completely stock Ubuntu install from USB.  Is there a way I can verify?

---

### Post by ubuuser3482 on 2024-08-13
> **oldfred said:**
> When installing grub uses efibootmgr to make "ubuntu" the first & default boot entry.
With HP it often works once & then HP resets boot to Windows.

Look in UEFI settings(not UEFI boot menu) and change boot order there.

Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)
HP Pavilion Plus 14  UEFI boot order for Ubuntu with Windows 11
[https://askubuntu.com/questions/1464469/windows-11-dual-boot-with-ubuntu-does-not-show-boot-menu/1465075#1465075](https://askubuntu.com/questions/1464469/windows-11-dual-boot-with-ubuntu-does-not-show-boot-menu/1465075#1465075)

When I installed Ubuntu I selected the option to reformat the entire drive and only install Ubuntu.  So there should be no remnants of Windows on this system.  Also, wouldn't this prevent all boots?  I only have problems on restarts.  Cold boots work perfectly.

---

### Post by ubuuser3482 on 2024-08-13
> **ubuuser3482 said:**
> No customization.  Completely stock Ubuntu install from USB.  Is there a way I can verify?

```

$ loginctl show-session $(loginctl | grep $(whoami) | awk '{print $1}') -p Type

Type=wayland

```

```

$ echo $XDG_SESSION_TYPE
wayland

```


You are correct, I'm running Wayland.  So the X Server log is a red herring?  Why would it even try to start X Server then if I am running Wayland?  This also makes me wonder if it's falling back to x11 on restarts for some reason if for example it can't use Wayland then?

---

### Post by ubuuser3482 on 2024-08-13
> **grahammechanical said:**
> Ubuntu 24.04 LTS usually defaults to using the Wayland windowing system and not the X-Server. Have you chosen to switch to using the X-Server?

Regards

You're definitely onto something here when I look in my /var/log/syslog.  I can see some lines related to the wayland shutdown from during the shutdown part of the restart procedure like:

```

2024-08-13T10:48:34.900860-06:00 systemd[1693]: Stopped target gnome-session-wayland@ubuntu.target - GNOME Wayland Session (session: ubuntu).

```

then as it hits the startup part of the restart procedure in the logs I start seeing
```

2024-08-13T10:48:56.934427-06:00 systemd[1]: Starting gdm.service - GNOME Display Manager...

```

followed shortly by the first appearance of the x server mention in the logs
```

2024-08-13T10:49:07.618591-06:00 /usr/libexec/gdm-x-session[1068]: (--) Log file renamed from "/var/log/Xorg.pid-1068.log" to "/var/log/Xorg.0.log"
2024-08-13T10:49:07.619295-06:00 /usr/libexec/gdm-x-session[1068]: X.Org X Server 1.21.1.11

```

Notice the timestamps from the Wayland stopping to the startup of the display manager to the x server.  So something is happening during restart and only during restart to make it suddenly choose x11 instead of wayland.  It's hard to know what matters in the logs but I don't see any log lines saying why it switched.

---

### Post by ubuuser3482 on 2024-08-13
> **ubuuser3482 said:**
> 
You are correct, I'm running Wayland.  So the X Server log is a red herring?  Why would it even try to start X Server then if I am running Wayland?  This also makes me wonder if it's falling back to x11 on restarts for some reason if for example it can't use Wayland then?

Ok looking at the logs I can confirm the following:

_**Cold Boot (success case):**_
Shortly after systemd starts then the logs show wayland starting (logs from gnome-shell and gdm-wayland-session and none from gdm-x-session)

_**Restart Boot (failure case):**_
Shortly after systemd starts then the logs immediately show an X Server failure.  (lots of logs from gdm-x-session and none from gnome-shell and gdm-wayland-session)

So it seems the problem is the **restart tries and fails to start Xorg whereas the cold boot tries and succeeds starting Wayland**.  Any idea how to determine why it chooses to start one in the cold boot and another in the restart boot?

---

### Post by ubuuser3482 on 2024-08-13
> **ubuuser3482 said:**
> Ok looking at the logs I can confirm the following:

_**Cold Boot (success case):**_
Shortly after systemd starts then the logs show wayland starting (logs from gnome-shell and gdm-wayland-session and none from gdm-x-session)

_**Restart Boot (failure case):**_
Shortly after systemd starts then the logs immediately show an X Server failure.  (lots of logs from gdm-x-session and none from gnome-shell and gdm-wayland-session)

So it seems the problem is the **restart tries and fails to start Xorg whereas the cold boot tries and succeeds starting Wayland**.  Any idea how to determine why it chooses to start one in the cold boot and another in the restart boot?

I noticed one other error which definitely seems related.  I only see it in the restart logs and not the cold boot logs and I pretty sure it corresponds to my Intel onboard video graphics driver
```

i915 0000:00:02.0: [drm] *ERROR* crtc 51: Can't calculate constants, dotclock = 0!

```

That error might be the explanation for the difference between cold boot and restart boot.  I have zero clue what it means and why it only happens on restarts and not cold starts.

---

### Post by ubuuser3482 on 2024-08-13
> **ubuuser3482 said:**
> I noticed one other error which definitely seems related.  I only see it in the restart logs and not the cold boot logs and I pretty sure it corresponds to my Intel onboard video graphics driver
```

i915 0000:00:02.0: [drm] *ERROR* crtc 51: Can't calculate constants, dotclock = 0!

```

That error might be the explanation for the difference between cold boot and restart boot.  I have zero clue what it means and why it only happens on restarts and not cold starts.

This bug from 2021 with the fix and the comment seems very relevant and it might be the exact same:

[https://askubuntu.com/questions/1321469/blank-no-signal-display-on-new-asus-z590-motherboard#comment2263701_1328010](https://askubuntu.com/questions/1321469/blank-no-signal-display-on-new-asus-z590-motherboard#comment2263701_1328010)

Unfortunately I have no idea how to tell if the reboot problem ever got fixed in the last two years after that comment was made.

---


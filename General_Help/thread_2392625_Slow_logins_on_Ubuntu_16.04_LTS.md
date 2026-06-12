---
title: "Slow logins on Ubuntu 16.04 LTS"
date: 2018-05-23
forum: General Help
---

### Post by anamjoshi on 2018-05-23
I am getting the following error in syslog

May 22 16:19:22 UB005 gnome-session-binary[22697]: WARNING: Unable to inhibit system: GDBus.Error:org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.freedesktop.login1': timed out
May  22 16:19:22 UB005 gnome-session[22697]: gnome-session-binary[22697]:  WARNING: Unable to inhibit system: GDBus.Error:org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.freedesktop.login1': timed out
May  22 16:19:22 UB005 dbus[1609]: [system] Activating via systemd: service  name='org.freedesktop.login1' unit='dbus-org.freedesktop.login1.service'
May 22 16:19:22 UB005 systemd[1]: Started Login Service.


Users logging via RDP or SSH experience slowness or they are not able to login at all.

**Here is status for various system services:**

**systemctl status dbus-org.freedesktop.login1.**
service
&#9679; systemd-logind.service - Login Service
   Loaded: loaded (/lib/systemd/system/systemd-logind.service; static; vendor preset: enabled)
   Active: active (running) since Tue 2018-05-22 14:07:24 IST; 2h 2min ago
     Docs: man:systemd-logind.service(8)
           man:logind.conf(5)
           [http://www.freedesktop.org/wiki/Software/systemd/logind](http://www.freedesktop.org/wiki/Software/systemd/logind)
           [http://www.freedesktop.org/wiki/Software/systemd/multiseat](http://www.freedesktop.org/wiki/Software/systemd/multiseat)
 Main PID: 1717 (systemd-logind)
   Status: "Processing requests..."
    Tasks: 1
   Memory: 1.9M
      CPU: 638ms
   CGroup: /system.slice/systemd-logind.service
           &#9492;&#9472;1717 /lib/systemd/systemd-logind

May 22 16:05:32 UB005 systemd-logind[1717]: New seat seat-vseat68.
May 22 16:05:54 UB005 systemd[1]: Started Login Service.
May 22 16:06:29 UB005 systemd[1]: Started Login Service.
May 22 16:06:54 UB005 systemd[1]: Started Login Service.
May 22 16:07:19 UB005 systemd-logind[1717]: New seat seat-vseat69.
May 22 16:07:21 UB005 systemd[1]: Started Login Service.
May 22 16:07:53 UB005 systemd[1]: Started Login Service.
May 22 16:08:34 UB005 systemd[1]: Started Login Service.
May 22 16:09:02 UB005 systemd[1]: Started Login Service.
May 22 16:09:39 UB005 systemd[1]: Started Login Service.


**busctl**

NAME                          
             PID PROCESS         USER             CONNECTION    UNIT                      SESSION    DESCRIPTION        
:1.0                                         1 systemd         root             :1.0          init.scope                -          -                  
:1.100                                    2212 upowerd         root             :1.100        upower.service            -          -                  
:1.1001                                  24876 unity-fallback- ashok.pandarkar  :1.1001       session-c19.scope         c19        -                  
:1.1002                                  24948 gvfs-udisks2-vo ashok.pandarkar  :1.1002       session-c19.scope         c19        -                  
org.freedesktop.DisplayManager             1736 lightdm         root             :1.15          lightdm.service           -          -                  
org.freedesktop.ModemManager1             1582 ModemManager    root             :1.4          ModemManager.service      -          -                  
org.freedesktop.NetworkManager             1649 NetworkManager  root             :1.7           NetworkManager.service    -          -                  
org.freedesktop.PackageKit                   - -               -                (activatable) -                         -         
org.freedesktop.PolicyKit1                1689 polkitd         root             :1.6          polkitd.service           -          -                  
org.freedesktop.RealtimeKit1              2194 rtkit-daemon    root             :1.95         rtkit-daemon.service      -          -                  
org.freedesktop.UDisks2                   3536 udisksd         root             :1.170        udisks2.service           -          -                  
org.freedesktop.UPower                    2212 upowerd         root             :1.100        upower.service            -          -                  
org.freedesktop.fwupd                     3547 fwupd           root             :1.172        dbus.service              -          -                  
org.freedesktop.hostname1                    - -               -                (activatable) -                         -         
org.freedesktop.locale1                      - -               -                (activatable) -                         -         
_*org.freedesktop.login1                       - -               -                (activatable) -                         -         *_
org.freedesktop.network1                     - -               -                (activatable) -                         -         
org.freedesktop.nm_dispatcher                - -               -                (activatable) -                         -         
org.freedesktop.realmd                       - -               -                (activatable) -                         -         
org.freedesktop.resolve1                     - -               -                (activatable) -                         -         
org.freedesktop.systemd1                     1 systemd         root             :1.0          init.scope                -          -                  
org.freedesktop.thermald                     - -               -                (activatable) -                         -         





**journalctl -u dbus**

May 22 16:18:10 UB005 dbus[1609]: [system]  Activating via systemd: service name='org.freedesktop.login1'  unit='dbus-org.freedesktop.login1.service'
May 22 16:18:23 UB005 dbus[1609]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
May 22 16:18:24 UB005 dbus[1609]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 22 16:18:35 UB005 dbus[1609]: [system] Failed to activate service 'org.freedesktop.login1': timed out
May  22 16:18:57 UB005 dbus[1609]: [system] Activating via systemd: service  name='org.freedesktop.login1' unit='dbus-org.freedesktop.login1.service'
May 22 16:19:22 UB005 dbus[1609]: [system] Failed to activate service 'org.freedesktop.login1': timed out
May  22 16:19:22 UB005 dbus[1609]: [system] Activating via systemd: service  name='org.freedesktop.login1' unit='dbus-org.freedesktop.login1.service'
May 22 16:19:26 UB005 dbus[1609]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
May 22 16:19:28 UB005 dbus[1609]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 22 16:19:47 UB005 dbus[1609]: [system] Failed to activate service 'org.freedesktop.login1': timed out
May  22 16:20:02 UB005 dbus[1609]: [system] Activating via systemd: service  name='org.freedesktop.login1' unit='dbus-org.freedesktop.login1.service'
May 22 16:20:27 UB005 dbus[1609]: [system] Failed to activate service 'org.freedesktop.login1': timed out
May  22 16:20:27 UB005 dbus[1609]: [system] Activating via systemd: service  name='org.freedesktop.login1' unit='dbus-org.freedesktop.login1.service'
May 22 16:20:52 UB005 dbus[1609]: [system] Failed to activate service 'org.freedesktop.login1': timed out
May  22 16:20:52 UB005 dbus[1609]: [system] Activating via systemd: service  name='org.freedesktop.login1' unit='dbus-org.freedesktop.login1.service'
May 22 16:21:17 UB005 dbus[1609]: [system] Failed to activate service 'org.freedesktop.login1': timed out
May  22 16:21:17 UB005 dbus[1609]: [system] Activating via systemd: service  name='org.freedesktop.login1' unit='dbus-org.freedesktop.login1.service'

---


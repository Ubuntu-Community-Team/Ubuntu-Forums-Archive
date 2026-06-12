---
title: "Occasional Complete System Freze"
date: 2020-08-30
forum: General Help
---

### Post by maglin2 on 2020-08-30
A few times now my wife's laptop (Ubuntu 20.04) has frozen. 
Screen freeze, keyboard unresponsive, can't change tty, even magic alt sysreq REISUB combination  does nothing.
The only way out is long press of the power button.
She's always been running firefox at the time, but that's the only app she ever uses, so I doubt that means much.
Normally the panels/bar (and clock) are hidden, but this time the time was displayed - 11:17:20
Checking the log viewer for that time the only thing within a minute seems to be a cron authorisation

11:17:01 cron: pam_unix(cron:session): session opened for user root by (uid=0)

Then I can see no other entries until reboot at 11.33.

Any help in figuring out what is going on would be much appreciated - hardware or software, and how to tell?
How to investigate what the cron job was authorising?
What else to look for next time it happens?

Thanks

---

### Post by tea for one on 2020-08-30
I can't help you with cron jobs but I can help you with REISUB.

Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a file:-

```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```

Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by maglin2 on 2020-08-30
Thanks for that. It might allow a more dignified exit come the next freeze.
The question of how to go about investigating the cause remains.

---

### Post by TheFu on 2020-08-30
Common crashes are due to hw failures or out of memory conditions.
And overview of the system would be helpful.

inxi -Fxxz

top, free, dmesg and journalctl should be helpful too.

---

### Post by maglin2 on 2020-08-31
Thanks for taking an interest. 

Here's the output of inxi, top and free.

```
$ inxi -Fxxz
System:    Kernel: 5.4.0-42-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.4 wm: gnome-shell dm: GDM3 
           Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Star Labs product: Lite v: N/A serial: <filter> Chassis: type: 10 serial: <filter> 
           Mobo: Star Labs Online Limited model: Star Lite Mk II serial: <filter> UEFI: American Megatrends v: 1.2.00 
           date: 03/05/2020 
Battery:   ID-1: BAT0 charge: 29.8 Wh condition: 30.4/30.4 Wh (100%) volts: 8.7/7.6 model: Intel SR 1 SR Real Battery 
           serial: <filter> status: Charging 
CPU:       Topology: Quad Core model: Intel Pentium N4200 bits: 64 type: MCP arch: Goldmont rev: 9 L2 cache: 1024 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 8755 
           Speed: 766 MHz min/max: 800/2500 MHz Core speeds (MHz): 1: 789 2: 786 3: 771 4: 752 
Graphics:  Device-1: Intel Celeron N3350/Pentium N4200/Atom E3900 Series Integrated Graphics driver: i915 v: kernel 
           bus ID: 00:02.0 chip ID: 8086:5a84 
           Display: wayland server: X.Org 1.20.8 driver: i915 compositor: gnome-shell resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel HD Graphics 505 (APL 3) v: 4.6 Mesa 20.0.8 direct render: Yes 
Audio:     Device-1: Intel Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster vendor: Realtek driver: snd_hda_intel 
           v: kernel bus ID: 00:0e.0 chip ID: 8086:5a98 
           Device-2: Alcor Micro USB2.0 Camera type: USB driver: snd-usb-audio,uvcvideo bus ID: 1-7:3 chip ID: 058f:3981 
           Sound Server: ALSA v: k5.4.0-42-generic 
Network:   Device-1: Intel Wireless 3165 driver: iwlwifi v: kernel port: f040 bus ID: 01:00.0 chip ID: 8086:3165 
           IF: wlp1s0 state: up mac: <filter> 
Drives:    Local Storage: total: 223.57 GiB used: 7.56 GiB (3.4%) 
           ID-1: /dev/sda vendor: Seagate model: Star Drive SATA SSD size: 223.57 GiB speed: 6.0 Gb/s serial: <filter> 
Partition: ID-1: / size: 216.88 GiB used: 7.35 GiB (3.4%) fs: ext4 dev: /dev/dm-1 
           ID-2: /boot size: 704.5 MiB used: 202.7 MiB (28.8%) fs: ext4 dev: /dev/sda2 
           ID-3: swap-1 size: 976.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-2 
Sensors:   System Temperatures: cpu: 46.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 230 Uptime: 1h 18m Memory: 7.61 GiB used: 1.14 GiB (14.9%) Init: systemd v: 245 runlevel: 5 Compilers: 
           gcc: 9.3.0 alt: 9 Shell: bash v: 5.0.17 running in: gnome-terminal inxi: 3.0.38 
```

```
$ top

top - 10:53:25 up  1:20,  1 user,  load average: 1.05, 0.54, 0.37
Tasks: 229 total,   1 running, 228 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.3 us,  7.1 sy,  0.0 ni, 87.1 id,  0.0 wa,  0.0 hi,  1.4 si,  0.0 st
MiB Mem :   7789.0 total,   5245.5 free,   1047.3 used,   1496.2 buff/cache
MiB Swap:    976.0 total,    976.0 free,      0.0 used.   6081.0 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                          
  10050 gill      20   0 4891144 262252 115608 S  12.5   3.3   1:50.70 gnome-shell                                                                                      
  10983 gill      20   0  420340  58808  45004 S  12.5   0.7   0:25.48 gnome-terminal-                                                                                  
  11347 gill      20   0   20672   4056   3384 R  12.5   0.1   0:00.03 top                                                                                              
  10350 gill      20   0  467044   8344   6856 S   6.2   0.1   0:01.69 ibus-daemon                                                                                      
  10452 gill      20   0 3038100 388016 213412 S   6.2   4.9   1:20.36 MainThread                                                                                       
      1 root      20   0  169024  13204   8484 S   0.0   0.2   0:13.25 systemd                                                                                          
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kthreadd                                                                                         
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                                                                           
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                                                                       
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-kblockd                                                                             
      9 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq                                                                                     
     10 root      20   0       0      0      0 S   0.0   0.0   0:00.15 ksoftirqd/0                                                                                      
     11 root      20   0       0      0      0 I   0.0   0.0   0:04.96 rcu_sched                                                                                        
     12 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/0                                                                                      
     13 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                                    
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                          
     15 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                          
     16 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                                    
     17 root      rt   0       0      0      0 S   0.0   0.0   0:00.33 migration/1                                                                                      
     18 root      20   0       0      0      0 S   0.0   0.0   0:00.17 ksoftirqd/1                                                                                      
     20 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-kblockd                                                                             
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                                                                          
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                                                                                    
     23 root      rt   0       0      0      0 S   0.0   0.0   0:00.34 migration/2                                                                                      
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.13 ksoftirqd/2                                                                                      
     26 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0H-kblockd                                                                             
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                                                                          
     28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                                                                                    
     29 root      rt   0       0      0      0 S   0.0   0.0   0:00.34 migration/3                                                                                      
     30 root      20   0       0      0      0 S   0.0   0.0   0:00.10 ksoftirqd/3                                                                                      
     32 root       0 -20       0      0      0 I   0.0   0.0   0:00.35 kworker/3:0H-events_highpri                                                                      
     33 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kdevtmpfs                                                                                        
     34 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns                                                                                            
     35 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_kthre                                                                                  
     36 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kauditd                                                                                          
     37 root      20   0       0      0      0 S   0.0   0.0   0:00.00 khungtaskd                                                                                       
     38 root      20   0       0      0      0 S   0.0   0.0   0:00.00 oom_reaper                                                                                       
     39 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 writeback   
```

```
$ free
              total        used        free      shared  buff/cache   available
Mem:        7975960     1098788     5366656      381104     1510516     6222320
Swap:        999420           0      999420
```


dmesg and journalctl seem too big to post. I'll look into how to link to dmesg and output only relevant timeframe for journalctl.

---

### Post by maglin2 on 2020-08-31
Here is some of journalctl output over relevant period to reboot

```
Aug 30 11:08:10 gill-Lite systemd[3931]: Started GNOME Session Manager (session: ubuntu).
Aug 30 11:08:10 gill-Lite systemd[3931]: Reached target GNOME Session Manager is ready.
Aug 30 11:08:10 gill-Lite systemd[3931]: Starting GNOME Shell on Wayland...
Aug 30 11:08:10 gill-Lite rtkit-daemon[1281]: Supervising 6 threads of 2 processes of 2 users.
Aug 30 11:08:10 gill-Lite rtkit-daemon[1281]: Successfully made thread 4088 of process 3945 owned by '1000' RT at priority 5.
Aug 30 11:08:10 gill-Lite rtkit-daemon[1281]: Supervising 7 threads of 2 processes of 2 users.
Aug 30 11:08:10 gill-Lite rtkit-daemon[1281]: Supervising 7 threads of 2 processes of 2 users.
Aug 30 11:08:10 gill-Lite rtkit-daemon[1281]: Successfully made thread 4090 of process 3945 owned by '1000' RT at priority 5.
Aug 30 11:08:10 gill-Lite rtkit-daemon[1281]: Supervising 8 threads of 2 processes of 2 users.
Aug 30 11:08:11 gill-Lite rtkit-daemon[1281]: Supervising 7 threads of 2 processes of 2 users.
Aug 30 11:08:12 gill-Lite rtkit-daemon[1281]: Successfully made thread 4095 of process 3945 owned by '1000' RT at priority 5.
Aug 30 11:08:12 gill-Lite rtkit-daemon[1281]: Supervising 8 threads of 2 processes of 2 users.
Aug 30 11:08:12 gill-Lite gnome-shell[4080]: Unset XDG_SESSION_ID, getCurrentSessionProxy() called outside a user session. Asking logind directly.
Aug 30 11:08:12 gill-Lite gnome-shell[4080]: Will monitor session 6
Aug 30 11:08:12 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating service name='org.freedesktop.portal.IBus' requested by ':1.32' (uid=1000 pid=4111 >
Aug 30 11:08:12 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.freedesktop.portal.IBus'
Aug 30 11:08:12 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating via systemd: service name='org.freedesktop.impl.portal.PermissionStore' unit='xdg-p>
Aug 30 11:08:12 gill-Lite systemd[3931]: Starting sandboxed app permission store...
Aug 30 11:08:12 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating service name='org.gnome.Shell.CalendarServer' requested by ':1.30' (uid=1000 pid=40>
Aug 30 11:08:12 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.freedesktop.impl.portal.PermissionStore'
Aug 30 11:08:12 gill-Lite systemd[3931]: Started sandboxed app permission store.
Aug 30 11:08:12 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating via systemd: service name='org.gnome.evolution.dataserver.Sources5' unit='evolution>
Aug 30 11:08:12 gill-Lite systemd[3931]: Starting Evolution source registry...
Aug 30 11:08:12 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.gnome.evolution.dataserver.Sources5'
Aug 30 11:08:12 gill-Lite systemd[3931]: Started Evolution source registry.
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar8' unit='evolutio>
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting Evolution calendar service...
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.gnome.Shell.CalendarServer'
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.gnome.evolution.dataserver.Calendar8'
Aug 30 11:08:13 gill-Lite systemd[3931]: Started Evolution calendar service.
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating service name='ca.desrt.dconf' requested by ':1.39' (uid=1000 pid=4148 comm="/usr/li>
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'ca.desrt.dconf'
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating via systemd: service name='org.gnome.evolution.dataserver.AddressBook10' unit='evol>
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting Evolution address book service...
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.gnome.evolution.dataserver.AddressBook10'
Aug 30 11:08:13 gill-Lite systemd[3931]: Started Evolution address book service.
Aug 30 11:08:13 gill-Lite dbus-daemon[1037]: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.124' (uid>
Aug 30 11:08:13 gill-Lite systemd[1]: Starting Location Lookup Service...
Aug 30 11:08:13 gill-Lite polkitd(authority=local)[1053]: Registered Authentication Agent for unix-session:6 (system bus name :1.124 [/usr/bin/gnome-shell], object pat>
Aug 30 11:08:13 gill-Lite gnome-shell[4080]: Telepathy is not available, chat integration will be disabled.
Aug 30 11:08:13 gill-Lite dbus-daemon[1037]: [system] Successfully activated service 'org.freedesktop.GeoClue2'
Aug 30 11:08:13 gill-Lite systemd[1]: Started Location Lookup Service.
Aug 30 11:08:13 gill-Lite dbus-daemon[1037]: [system] Activating via systemd: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.124'>
Aug 30 11:08:13 gill-Lite systemd[1]: Starting PackageKit Daemon...
Aug 30 11:08:13 gill-Lite PackageKit[4179]: daemon start
Aug 30 11:08:13 gill-Lite dbus-daemon[1037]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Aug 30 11:08:13 gill-Lite systemd[1]: Started PackageKit Daemon.
Aug 30 11:08:13 gill-Lite systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating service name='org.freedesktop.FileManager1' requested by ':1.30' (uid=1000 pid=4080>
Aug 30 11:08:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating service name='org.gnome.Shell.Notifications' requested by ':1.30' (uid=1000 pid=408>
Aug 30 11:08:13 gill-Lite at-spi-dbus-bus.desktop[4089]: dbus-daemon[4089]: Activating service name='org.a11y.atspi.Registry' requested by ':1.0' (uid=1000 pid=4080 co>
Aug 30 11:08:13 gill-Lite at-spi-dbus-bus.desktop[4089]: dbus-daemon[4089]: Successfully activated service 'org.a11y.atspi.Registry'
Aug 30 11:08:13 gill-Lite at-spi-dbus-bus.desktop[4200]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Aug 30 11:08:13 gill-Lite systemd[3931]: Started GNOME Shell on Wayland.
Aug 30 11:08:13 gill-Lite systemd[3931]: Reached target GNOME Shell on Wayland.
Aug 30 11:08:13 gill-Lite systemd[3931]: Reached target GNOME Session is initialized.
Aug 30 11:08:13 gill-Lite systemd[3931]: Reached target GNOME Wayland Session.
Aug 30 11:08:13 gill-Lite systemd[3931]: Reached target GNOME Session (session: ubuntu).
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting Signal initialization done to GNOME Session Manager...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Accessibility settings...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Color management...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Date & Time handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Maintenance of expirable data...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Keyboard handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Media keys handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Power management handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Printer notifications...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME RFKill handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Freedesktop screensaver handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Sharing handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Smartcard handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Sound sample caching handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME USB protection handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME Wacom handling...
Aug 30 11:08:13 gill-Lite systemd[3931]: Starting GNOME WWan management...
Aug 30 11:08:13 gill-Lite systemd[3931]: gnome-session-signal-init.service: Succeeded.
Aug 30 11:08:13 gill-Lite systemd[3931]: Finished Signal initialization done to GNOME Session Manager.
Aug 30 11:08:13 gill-Lite systemd[3931]: Started GNOME Accessibility settings.
Aug 30 11:08:13 gill-Lite systemd[3931]: Started GNOME Maintenance of expirable data.
Aug 30 11:08:13 gill-Lite systemd[3931]: Reached target GNOME Accessibility settings.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME Maintenance of expirable data.
Aug 30 11:08:14 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.gnome.Shell.Notifications'
Aug 30 11:08:14 gill-Lite gnome-session-binary[4059]: Entering running state
Aug 30 11:08:14 gill-Lite dbus-daemon[1037]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' re>
Aug 30 11:08:14 gill-Lite systemd[1]: Starting Hostname Service...
Aug 30 11:08:14 gill-Lite NetworkManager[1038]: <info>  [1598782094.1460] agent-manager: agent[75e056e74444c182,:1.124/org.gnome.Shell.NetworkAgent/1000]: agent regist>
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME Freedesktop screensaver handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME Freedesktop screensaver handling.
Aug 30 11:08:14 gill-Lite at-spi2-registr[4200]: Failed to register client: GDBus.Error:org.gnome.SessionManager.AlreadyRegistered: Unable to register client
Aug 30 11:08:14 gill-Lite at-spi2-registr[4200]: Unable to register client with session manager
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME Smartcard handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME Smartcard handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME Date & Time handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME Date & Time handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME Sharing handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME Sharing handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME USB protection handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME WWan management.
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME Printer notifications.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME Printer notifications.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME USB protection handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME WWan management.
Aug 30 11:08:14 gill-Lite tracker-store.desktop[4288]: (uint32 2,)
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME Sound sample caching handling.
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME Sound sample caching handling.
Aug 30 11:08:14 gill-Lite dbus-daemon[1037]: [system] Successfully activated service 'org.freedesktop.hostname1'
Aug 30 11:08:14 gill-Lite systemd[1]: Started Hostname Service.
Aug 30 11:08:14 gill-Lite systemd[3931]: Started GNOME RFKill handling.
Aug 30 11:08:14 gill-Lite kernel: rfkill: input handler disabled
Aug 30 11:08:14 gill-Lite systemd[3931]: Reached target GNOME RFKill handling.
Aug 30 11:08:14 gill-Lite gnome-shell[4080]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
Aug 30 11:08:15 gill-Lite gnome-shell[4080]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
Aug 30 11:08:15 gill-Lite systemd[3931]: Started GNOME Keyboard handling.
Aug 30 11:08:15 gill-Lite systemd[3931]: Reached target GNOME Keyboard handling.
Aug 30 11:08:15 gill-Lite dbus-daemon[1037]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service' reques>
Aug 30 11:08:15 gill-Lite systemd[1]: Starting Locale Service...
Aug 30 11:08:15 gill-Lite systemd[3931]: Started GNOME Media keys handling.
Aug 30 11:08:15 gill-Lite systemd[3931]: Reached target GNOME Media keys handling.
Aug 30 11:08:15 gill-Lite systemd[3931]: Started GNOME Color management.
Aug 30 11:08:15 gill-Lite systemd[3931]: Reached target GNOME Color management.
Aug 30 11:08:15 gill-Lite gnome-shell[2995]: Failed to set CRTC gamma: drmModeCrtcSetGamma on CRTC 55 failed: Permission denied
Aug 30 11:08:15 gill-Lite dbus-daemon[1037]: [system] Successfully activated service 'org.freedesktop.locale1'
Aug 30 11:08:15 gill-Lite systemd[1]: Started Locale Service.
Aug 30 11:08:15 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.freedesktop.FileManager1'
Aug 30 11:08:15 gill-Lite gsd-media-keys[4232]: Failed to grab accelerator for keybinding settings:hibernate
Aug 30 11:08:15 gill-Lite gsd-media-keys[4232]: Failed to grab accelerator for keybinding settings:playback-random
Aug 30 11:08:15 gill-Lite gsd-media-keys[4232]: Failed to grab accelerator for keybinding settings:rfkill
Aug 30 11:08:15 gill-Lite gsd-media-keys[4232]: Failed to grab accelerator for keybinding settings:playback-repeat
Aug 30 11:08:15 gill-Lite colord[1818]: failed to get session [pid 4218]: No data available
Aug 30 11:08:15 gill-Lite gnome-shell[2995]: Failed to set CRTC gamma: drmModeCrtcSetGamma on CRTC 55 failed: Permission denied
Aug 30 11:08:16 gill-Lite systemd[3931]: Started GNOME Power management handling.
Aug 30 11:08:16 gill-Lite systemd[3931]: Reached target GNOME Power management handling.
Aug 30 11:08:16 gill-Lite systemd[3931]: Started GNOME Wacom handling.
Aug 30 11:08:16 gill-Lite systemd[3931]: Reached target GNOME Wacom handling.
Aug 30 11:08:16 gill-Lite systemd[3931]: Reached target GNOME Session.
Aug 30 11:08:16 gill-Lite systemd[3931]: Reached target GNOME Wayland Session (session: ubuntu).
Aug 30 11:08:16 gill-Lite systemd[3931]: Reached target Current graphical user session.
Aug 30 11:08:16 gill-Lite systemd[3931]: Condition check resulted in GNOME Initial Setup being skipped.
Aug 30 11:08:16 gill-Lite systemd[3931]: Condition check resulted in GNOME Welcome Tour being skipped.
Aug 30 11:08:16 gill-Lite systemd[3931]: Startup finished in 6.011s.
Aug 30 11:08:16 gill-Lite systemd[3931]: GNOME session X11 services is not active.
Aug 30 11:08:16 gill-Lite systemd[3931]: Dependency failed for GNOME XSettings.
Aug 30 11:08:16 gill-Lite systemd[3931]: gsd-xsettings.target: Job gsd-xsettings.target/start failed with result 'dependency'.
Aug 30 11:08:16 gill-Lite systemd[3931]: Starting GNOME XSettings...
Aug 30 11:08:16 gill-Lite gnome-shell[4402]: The XKEYBOARD keymap compiler (xkbcomp) reports:
Aug 30 11:08:16 gill-Lite gnome-shell[4402]: > Warning:          Unsupported maximum keycode 569, clipping.
Aug 30 11:08:16 gill-Lite gnome-shell[4402]: >                   X11 cannot support keycodes above 255.
Aug 30 11:08:16 gill-Lite gnome-shell[4402]: > Internal error:   Could not resolve keysym Invalid
Aug 30 11:08:16 gill-Lite gnome-shell[4402]: Errors from xkbcomp are not fatal to the X server
Aug 30 11:08:16 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating service name='org.freedesktop.portal.IBus' requested by ':1.81' (uid=1000 pid=4398 >
Aug 30 11:08:16 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.freedesktop.portal.IBus'
Aug 30 11:08:16 gill-Lite gnome-shell[4080]: GNOME Shell started at Sun Aug 30 2020 11:08:13 GMT+0100 (BST)
Aug 30 11:08:16 gill-Lite gnome-shell[4080]: Registering session with GDM
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Wayland Session (session: gnome-login).
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target Current graphical user session.
Aug 30 11:08:16 gill-Lite systemd[2900]: unicast-local-avahi.path: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped Path trigger for Avahi .local domain notifications.
Aug 30 11:08:16 gill-Lite systemd[2900]: update-notifier-crash.path: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped Path trigger for Apport crash notifications.
Aug 30 11:08:16 gill-Lite systemd[2900]: update-notifier-release.path: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped Path trigger for new release of Ubuntu notifications.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Session.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Wayland Session.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Session (session: gnome-login).
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Accessibility settings.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Color management.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Keyboard handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Media keys handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Power management handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Printer notifications.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME RFKill handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Smartcard handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Sound sample caching handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME USB protection handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Wacom handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME WWan management.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Accessibility settings...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Color management...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Keyboard handling...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Media keys handling...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Power management handling...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Printer notifications...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME RFKill handling...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Smartcard handling...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Sound sample caching handling...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME USB protection handling...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Wacom handling...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME WWan management...
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-usb-protection.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME USB protection handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-print-notifications.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Printer notifications.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-wacom.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Wacom handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-sound.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Sound sample caching handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-rfkill.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME RFKill handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-smartcard.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Smartcard handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-a11y-settings.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Accessibility settings.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-wwan.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME WWan management.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-power.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Power management handling.
Aug 30 11:08:16 gill-Lite systemd[3931]: Started GNOME XSettings.
Aug 30 11:08:16 gill-Lite gsd-color[4218]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/xrandr_Najing_CEC_Pan>
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-color.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Color management.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-keyboard.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Keyboard handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-media-keys.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Media keys handling.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Session is initialized.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Shell on Wayland.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Shell on Wayland...
Aug 30 11:08:16 gill-Lite gsd-xsettings[3207]: gsd-xsettings: Fatal IO error 11 (Resource temporarily unavailable) on X server :1025.
Aug 30 11:08:16 gill-Lite systemd[2900]: gnome-session-monitor.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped Monitor Session leader for GNOME Session.
Aug 30 11:08:16 gill-Lite gnome-shell[2995]: Connection to xwayland lost
Aug 30 11:08:16 gill-Lite gdm-launch-environment][2882]: pam_unix(gdm-launch-environment:session): session closed for user gdm
Aug 30 11:08:16 gill-Lite systemd[1]: session-c1.scope: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-xsettings.service: Main process exited, code=exited, status=1/FAILURE
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-xsettings.service: Failed with result 'exit-code'.
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-xsettings.service: Triggering OnFailure= dependencies.
Aug 30 11:08:16 gill-Lite systemd[2900]: Requested transaction contradicts existing jobs: Transaction for gnome-session-failed.target/start is destructive (graphical-s>
Aug 30 11:08:16 gill-Lite systemd[2900]: gsd-xsettings.service: Failed to enqueue OnFailure= job, ignoring: Transaction for gnome-session-failed.target/start is destru>
Aug 30 11:08:16 gill-Lite systemd-logind[1059]: Session c1 logged out. Waiting for processes to exit.
Aug 30 11:08:16 gill-Lite systemd-logind[1059]: Removed session c1.
Aug 30 11:08:16 gill-Lite gdm3[1165]: Child process -2917 was already dead.
Aug 30 11:08:16 gill-Lite systemd[2900]: pulseaudio.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: gnome-shell-wayland.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Shell on Wayland.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target GNOME Session Manager is ready.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping GNOME Session Manager (session: gnome-login)...
Aug 30 11:08:16 gill-Lite gnome-session[2980]: gnome-session-binary[2980]: WARNING: Could not get session class: No such device or address
Aug 30 11:08:16 gill-Lite gnome-session-binary[2980]: WARNING: Could not get session class: No such device or address
Aug 30 11:08:16 gill-Lite systemd[2900]: at-spi-dbus-bus.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: gnome-session-manager@gnome-login.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped GNOME Session Manager (session: gnome-login).
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target Tasks to be run before GNOME Session starts.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target Session services which should run early before the graphical session is brought up.
Aug 30 11:08:16 gill-Lite systemd[2900]: Reached target Shutdown running GNOME Session.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping Start gnome-keyring as SSH agent...
Aug 30 11:08:16 gill-Lite systemd[2900]: Starting Restart DBus after GNOME Session shutdown...
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped target Shutdown running GNOME Session.
Aug 30 11:08:16 gill-Lite systemd[2900]: Started Restart DBus after GNOME Session shutdown.
Aug 30 11:08:16 gill-Lite systemd[2900]: gnome-session-restart-dbus.service: Succeeded.
Aug 30 11:08:16 gill-Lite sh[4459]: dbus-update-activation-environment: error: unable to connect to D-Bus: Did not receive a reply. Possible causes include: the remote>
Aug 30 11:08:16 gill-Lite gvfsd[2937]: A connection to the bus can't be made
Aug 30 11:08:16 gill-Lite tracker-miner-fs[2911]: Received signal:15->'Terminated'
Aug 30 11:08:16 gill-Lite tracker-miner-f[2911]: Error while sending AddMatch() message: The connection is closed
Aug 30 11:08:16 gill-Lite tracker-miner-f[2911]: Error while sending AddMatch() message: The connection is closed
Aug 30 11:08:16 gill-Lite tracker-miner-f[2911]: Error while sending AddMatch() message: The connection is closed
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopping D-Bus User Message Bus...
Aug 30 11:08:16 gill-Lite systemd[2900]: run-user-125-gvfs.mount: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: gvfs-goa-volume-monitor.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: gvfs-mtp-volume-monitor.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[3931]: run-user-125-gvfs.mount: Succeeded.
Aug 30 11:08:16 gill-Lite tracker-miner-fs[2911]: OK
Aug 30 11:08:16 gill-Lite systemd[2900]: gvfs-metadata.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: dbus.service: Killing process 2996 (dconf worker) with signal SIGKILL.
Aug 30 11:08:16 gill-Lite systemd[2900]: gvfs-udisks2-volume-monitor.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[1]: run-user-125-gvfs.mount: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: gvfs-afc-volume-monitor.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: gvfs-gphoto2-volume-monitor.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: xdg-permission-store.service: Main process exited, code=exited, status=1/FAILURE
Aug 30 11:08:16 gill-Lite systemd[2900]: xdg-permission-store.service: Failed with result 'exit-code'.
Aug 30 11:08:16 gill-Lite systemd[2900]: gnome-keyring-ssh.service: Control process exited, code=exited, status=71/OSERR
Aug 30 11:08:16 gill-Lite systemd[2900]: gnome-keyring-ssh.service: Failed with result 'exit-code'.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped Start gnome-keyring as SSH agent.
Aug 30 11:08:16 gill-Lite systemd[2900]: gvfs-daemon.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: dbus.service: Succeeded.
Aug 30 11:08:16 gill-Lite systemd[2900]: Stopped D-Bus User Message Bus.
Aug 30 11:08:16 gill-Lite systemd[2900]: Started D-Bus User Message Bus.
Aug 30 11:08:16 gill-Lite dbus-daemon[4461]: [session uid=125 pid=4461] AppArmor D-Bus mediation is enabled
Aug 30 11:08:16 gill-Lite systemd[2900]: tracker-miner-fs.service: Succeeded.
Aug 30 11:08:17 gill-Lite polkitd(authority=local)[1053]: Unregistered Authentication Agent for unix-session:c1 (system bus name :1.85, object path /org/freedesktop/Po>
Aug 30 11:08:20 gill-Lite systemd[3931]: tracker-extract.service: Succeeded.
Aug 30 11:08:24 gill-Lite gnome-power-sta[4278]: ../../../../../gdk/x11/gdkwindow-x11.c:5633 drawable is not a native X11 window
Aug 30 11:08:24 gill-Lite gnome-power-sta[4278]: ../../../../../gdk/x11/gdkwindow-x11.c:5633 drawable is not a native X11 window
Aug 30 11:08:24 gill-Lite CRON[4464]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 30 11:08:24 gill-Lite CRON[4465]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; f>
Aug 30 11:08:24 gill-Lite CRON[4464]: pam_unix(cron:session): session closed for user root
Aug 30 11:08:26 gill-Lite systemd[1]: Stopping User Manager for UID 125...
Aug 30 11:08:26 gill-Lite systemd[2900]: Removed slice gnome\x2dsession\x2dmanager.slice.
Aug 30 11:08:26 gill-Lite systemd[2900]: Stopped target Main User Target.
Aug 30 11:08:26 gill-Lite systemd[2900]: Stopping D-Bus User Message Bus...
Aug 30 11:08:26 gill-Lite systemd[2900]: dbus.service: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Stopped D-Bus User Message Bus.
Aug 30 11:08:26 gill-Lite systemd[2900]: Stopped target Basic System.
Aug 30 11:08:26 gill-Lite systemd[2900]: Stopped target Paths.
Aug 30 11:08:26 gill-Lite systemd[2900]: ubuntu-report.path: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Stopped Pending report trigger for Ubuntu Report.
Aug 30 11:08:26 gill-Lite systemd[2900]: Stopped target Sockets.
Aug 30 11:08:26 gill-Lite systemd[2900]: Stopped target Timers.
Aug 30 11:08:26 gill-Lite systemd[2900]: dbus.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed D-Bus User Message Bus Socket.
Aug 30 11:08:26 gill-Lite systemd[2900]: dirmngr.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed GnuPG network certificate management daemon.
Aug 30 11:08:26 gill-Lite systemd[2900]: gpg-agent-browser.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed GnuPG cryptographic agent and passphrase cache (access for web browsers).
Aug 30 11:08:26 gill-Lite systemd[2900]: gpg-agent-extra.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed GnuPG cryptographic agent and passphrase cache (restricted).
Aug 30 11:08:26 gill-Lite systemd[2900]: gpg-agent-ssh.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed GnuPG cryptographic agent (ssh-agent emulation).
Aug 30 11:08:26 gill-Lite systemd[2900]: gpg-agent.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed GnuPG cryptographic agent and passphrase cache.
Aug 30 11:08:26 gill-Lite systemd[2900]: pk-debconf-helper.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed debconf communication socket.
Aug 30 11:08:26 gill-Lite systemd[2900]: pulseaudio.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed Sound System.
Aug 30 11:08:26 gill-Lite systemd[2900]: snapd.session-agent.socket: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Closed REST API socket for snapd user session agent.
Aug 30 11:08:26 gill-Lite systemd[2900]: Reached target Shutdown.
Aug 30 11:08:26 gill-Lite systemd[2900]: systemd-exit.service: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[2900]: Finished Exit the Session.
Aug 30 11:08:26 gill-Lite systemd[2900]: Reached target Exit the Session.
Aug 30 11:08:26 gill-Lite systemd[1]: user@125.service: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[1]: Stopped User Manager for UID 125.
Aug 30 11:08:26 gill-Lite systemd[1]: Stopping User Runtime Directory /run/user/125...
Aug 30 11:08:26 gill-Lite systemd[3931]: run-user-125.mount: Succeeded.
Aug 30 11:08:26 gill-Lite systemd[1]: run-user-125.mount: Succeeded.
Aug 30 11:08:27 gill-Lite systemd[1]: user-runtime-dir@125.service: Succeeded.
Aug 30 11:08:27 gill-Lite systemd[1]: Stopped User Runtime Directory /run/user/125.
Aug 30 11:08:27 gill-Lite systemd[1]: Removed slice User Slice of UID 125.
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/firefox.profile
Aug 30 11:08:31 gill-Lite systemd[3931]: Started Application launched by gsd-media-keys.
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/whitelist-usr-share-common.inc
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/firefox-common.profile
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/disable-common.inc
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/disable-devel.inc
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/disable-exec.inc
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/disable-interpreters.inc
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/disable-programs.inc
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/whitelist-common.inc
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Reading profile /etc/firejail/whitelist-var-common.inc
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Warning: networking feature is disabled in Firejail configuration file
Aug 30 11:08:31 gill-Lite gsd-media-keys[4486]: Parent pid 4486, child pid 4489
Aug 30 11:08:31 gill-Lite gsd-media-keys[4489]: Warning: An abstract unix socket for session D-BUS might still be available. Use --net or remove unix from --protocol s>
Aug 30 11:08:31 gill-Lite gsd-media-keys[4493]: Warning: cleaning all supplementary groups
Aug 30 11:08:31 gill-Lite gsd-media-keys[4494]: Warning: cleaning all supplementary groups
Aug 30 11:08:31 gill-Lite gsd-media-keys[4489]: Post-exec seccomp protector enabled
Aug 30 11:08:31 gill-Lite gsd-media-keys[4495]: Seccomp list in: !chroot, check list: @default-keep, prelist: unknown,
Aug 30 11:08:31 gill-Lite gsd-media-keys[4497]: Child process initialized in 125.75 ms
Aug 30 11:08:32 gill-Lite systemd[1]: fprintd.service: Succeeded.
Aug 30 11:08:41 gill-Lite tracker-store[4062]: OK
Aug 30 11:08:41 gill-Lite systemd[3931]: tracker-store.service: Succeeded.
Aug 30 11:08:45 gill-Lite systemd[1]: systemd-hostnamed.service: Succeeded.
Aug 30 11:08:45 gill-Lite systemd[1]: systemd-localed.service: Succeeded.
Aug 30 11:08:55 gill-Lite kernel: [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:84:a1:d1:63:14:c2:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TT>
Aug 30 11:09:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' reque>
Aug 30 11:09:13 gill-Lite systemd[3931]: Starting Virtual filesystem metadata service...
Aug 30 11:09:13 gill-Lite dbus-daemon[3952]: [session uid=1000 pid=3952] Successfully activated service 'org.gtk.vfs.Metadata'
Aug 30 11:09:13 gill-Lite systemd[3931]: Started Virtual filesystem metadata service.
Aug 30 11:11:00 gill-Lite kernel: [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:84:a1:d1:63:14:c2:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TT>
Aug 30 11:13:05 gill-Lite kernel: [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:84:a1:d1:63:14:c2:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TT>
Aug 30 11:13:18 gill-Lite PackageKit[4179]: daemon quit
Aug 30 11:13:18 gill-Lite systemd[1]: packagekit.service: Succeeded.
Aug 30 11:15:10 gill-Lite kernel: [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:84:a1:d1:63:14:c2:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TT>
Aug 30 11:17:01 gill-Lite CRON[4887]: pam_unix(cron:session): session opened for user root by (uid=0)
-- Reboot --
Aug 30 11:33:22 gill-Lite kernel: Linux version 5.4.0-42-generic (buildd@lgw01-amd64-038) (gcc version 9.3.0 (Ubuntu 9.3.0-10ubuntu2)) #46-Ubuntu SMP Fri Jul 10 00:24:>
Aug 30 11:33:22 gill-Lite kernel: Command line: BOOT_IMAGE=/vmlinuz-5.4.0-42-generic root=/dev/mapper/vgubuntu-root ro quiet splash vt.handoff=7
Aug 30 11:33:22 gill-Lite kernel: KERNEL supported cpus:
Aug 30 11:33:22 gill-Lite kernel:   Intel GenuineIntel
Aug 30 11:33:22 gill-Lite kernel:   AMD AuthenticAMD
Aug 30 11:33:22 gill-Lite kernel:   Hygon HygonGenuine
Aug 30 11:33:22 gill-Lite kernel:   Centaur CentaurHauls
Aug 30 11:33:22 gill-Lite kernel:   zhaoxin   Shanghai 
```

---

### Post by Autodave on 2020-08-31
In Firefox, disable all ad blockers and then enable this: uBlock.  That may help., won't hurt.

To me, my first guess would be memory chip failing.  Make sure that laptop is getting air through the vents and that she is not holding on her lap or anything soft that can block the vents.

---

### Post by TheFu on 2020-08-31
The output for the monitoring commands needs to happen while the same programs are running as when the system freezes. Looks like the data above was run when the system wasn't doing anything. Where's the web browser in the process table?  Really, we only need to see the top 10-15 processes AND only those when the system is busy.

On a CPU like that, I wouldn't use Gnome3. I'd run XFCE or no DE at all to keep the system as fast as possible. Gnome3 is a bloated DE, especially for a CPU with about 2000 passmarks.

I think 1G of swap is not sufficient for any Ubuntu desktop. I always setup 4.1G swap these days regardless of RAM. Less and a browser with lots of tabs will crash the system without enough "slowing system" feedback before hand. Any more and it is wasting storage.  The point of swap is to let the user "feel" the system getting slower as RAM is exhausted.  It is still up to the user to close programs to prevent a crash.  SSDs are so much faster than spinning HDDs, so we humans need a little more time to notice the issue as it happens, hence the need for a larger, 4.1G swap.  I had a few laptops with 1500-3000 passmarks, 2G or 4G of RAM, running a lite Ubuntu version (Ubuntu-Mate) that would crash about once a month.  They had the default, whatever-the-installer-created amount of swap.  Usually, the systems would get really, really, really, slow for about 2 minutes before becoming unresponsive.  Initially, I just gave each time to resolve the issue, which they never did. After 20 minutes, I'd have to power them off.  Then I increased the swap to 4.1G.  Never had that problem again, because it gave me more time to "feel" the system become slower. Usually, I'd be running FF and Thunderbird, plus a bunch of xterms.  Closing FF would be an inconvenience - lots of tabs still to be read, but closing thunderbird was an easy choice and usually freed about 1G of RAM.

Just some things to consider.

When looking through the system log files, look for errors and warnings.  Failing hardware usually will get something into the logs. The only HW faults that many not get into system logs would be failing storage. For that there is SMART - use smartctl to run a test, then wait until the test completes (2min - 4 hours) and use smartclt to ask for the test results. It is a long shot, but not hard.

---

### Post by maglin2 on 2020-08-31
> **Autodave said:**
> In Firefox, disable all ad blockers and then enable this: uBlock.  That may help., won't hurt.

To me, my first guess would be memory chip failing.  Make sure that laptop is getting air through the vents and that she is not holding on her lap or anything soft that can block the vents.

Thanks. For at least one freeze ublock origin was the only addon.

In any case for the last one the only tab open was bbc.co.uk - which has no ads - though I've noticed it does occasionally have some moderately cpu and RAM eating content.

This netbook has no fans and no vents - normal power consumption is 3.8 watts, and it never feels warm. I will figure out how to get cpu temp displayed continuously though. I suspect that will be far more of a challenge with gnome than it was with kde.

---

### Post by maglin2 on 2020-08-31
Thanks - lots to consider there. I'll work through it - I've jotted some initial thoughts below.

[I]The output for the monitoring commands needs  to happen while the same programs are running as when the system  freezes. Looks like the data above was run when the system wasn't doing  anything. Where's the web browser in the process table?  Really, we only  need to see the top 10-15 processes AND only those when the system is  busy.

[/I]inxi just relates to fixed properties  as far as I know, journalctl does cover the freeze period, so I guess  you are referring to top and free? I don't how I would get top or free  to autostart, log an iteration every so often to a text file, and delete  all but the last few to keep space used reasonable. I'll ponder it! 
By the way firefox was running for top - it goes by the process name Mainthread I think for some reason

[I]On a CPU like that, I wouldn't use Gnome3. I'd run XFCE or no DE at  all to keep the system as fast as possible. Gnome3 is a bloated DE,  especially for a CPU with about 2000 passmarks.
[/I]
I agree - though 20.04 does run really pretty well. More significantly  it's for my wife, and it is, I think, the most attractive and user  friendly Ubuntu interface for a novice (and frankly disinterested) user.  When it doesn't freeze she's delighted with it! 5 year support is  another plus  - reduces the change frequency. Her only OS experience  before this was a chromebook - which was simplicity itself and totally  bombproof, but is now AUE.  May yet have to buy another though.
I might try her with Xubuntu or Lubuntu if I do a reinstall.

*I think 1G of swap is not sufficient for any Ubuntu desktop. I  always setup 4.1G swap these days regardless of RAM. Less and a browser  with lots of tabs will crash the system without enough "slowing system"  feedback before hand. Any more and it is wasting storage.  The point of  swap is to let the user "feel" the system getting slower as RAM is  exhausted.  It is still up to the user to close programs to prevent a  crash.  SSDs are so much faster than spinning HDDs, so we humans need a  little more time to notice the issue as it happens, hence the need for a  larger, 4.1G swap.  I had a few laptops with 1500-3000 passmarks, 2G or  4G of RAM, running a lite Ubuntu version (Ubuntu-Mate) that would crash  about once a month.  They had the default,  whatever-the-installer-created amount of swap.  Usually, the systems  would get really, really, really, slow for about 2 minutes before  becoming unresponsive.  Initially, I just gave each time to resolve the  issue, which they never did. After 20 minutes, I'd have to power them  off.  Then I increased the swap to 4.1G.  Never had that problem again,  because it gave me more time to "feel" the system become slower.  Usually, I'd be running FF and Thunderbird, plus a bunch of xterms.   Closing FF would be an inconvenience - lots of tabs still to be read,  but closing thunderbird was an easy choice and usually freed about 1G of  RAM.*

This is something I think I might possibly be able to do something about!
[I]
Just some things to consider.

When looking through the system log files, look for errors and warnings.   Failing hardware usually will get something into the logs. The only HW  faults that many not get into system logs would be failing storage. For  that there is SMART - use smartctl to run a test, then wait until the  test completes (2min - 4 hours) and use smartclt to ask for the test  results. It is a long shot, but not hard.[/I]

I'll give that a shot too.

---

### Post by tea for one on 2020-08-31
Does this laptop have an M2 SSD or a 2.5" SSD?

From the freezing description in your original post, it seems similar to something I have experienced with an M2 2280 NVME  SSD.

I also intermittently had a completely frozen PC, unable to **Ctrl Alt T** for the terminal and also unable to access** tty**.

I had to use REISUB to power off but this also taints the EFI (FAT32) partition, which then had to be tidied up with a file system check & repair.

Fortunately, I have two drives in this PC and cloned my system to an older 2.5" SSD and the freezing does not happen any more.

I sent the NVME drive back to the supplier 7 days ago and they haven't yet replied.

Have you contacted Starlabs yet to see if they are aware of any faulty drives?

---

### Post by maglin2 on 2020-08-31
> **tea for one said:**
> Does this laptop have an M2 SSD or a 2.5" SSD?

From the freezing description in your original post, it seems similar to something I have experienced with an M2 2280 NVME  SSD.

I also intermittently had a completely frozen PC, unable to **Ctrl Alt T** for the terminal and also unable to access** tty**.

I had to use REISUB to power off but this also taints the EFI (FAT32) partition, which then had to be tidied up with a file system check & repair.

Fortunately, I have two drives in this PC and cloned my system to an older 2.5" SSD and the freezing does not happen any more.

I sent the NVME drive back to the supplier 7 days ago and they haven't yet replied.

Have you contacted Starlabs yet to see if they are aware of any faulty drives?

Sorry I don't know the answer to that. It just states '240GB Over-Provisioned SATA SSD'

So I suspect not NVME, but don't really know.

Contacting starlabs support is next on my list. Thought I'd ask here first though in case someone came up with a cunning diagnostic that pinned it to either hardware or OS. I'll also run a smartctl test as suggested by TheFu.

---

### Post by CatKiller on 2020-08-31
> **maglin2 said:**
> I will figure out how to get cpu temp displayed continuously though. I suspect that will be far more of a challenge with gnome than it was with kde.
Conky is good for that. It can query all kinds of stuff (or run arbitrary things) and draws the result onto the desktop. The things you're interested in are easily accomplished with conky objects.

---

### Post by TheFu on 2020-08-31
> **maglin2 said:**
> 
inxi just relates to fixed properties  as far as I know, journalctl does cover the freeze period, so I guess  you are referring to top and free? I don't how I would get top or free  to autostart, log an iteration every so often to a text file, and delete  all but the last few to keep space used reasonable. I'll ponder it! 
By the way firefox was running for top - it goes by the process name Mainthread I think for some reason

Yes. inxi is the system-info in a minimal format.  For example:
```
Seagate model: Star Drive SATA SSD
```
Tells us it is an SSD, using the SATA connection, not NVMe, from Seagate. I wouldn't read too much into this.  Lots of the SSD makers sell to other storage vendors who don't actually make SSDs.  I think there are only 4 SSD manufacturers in the world, so all the others are re-branded.

Didn't think my firefox doesn't show up as "MainThread", so that's new to me. The process table for some firefox processes on my desktop:
```
tf       22887 22624  1 Aug30 pts/2    00:20:20 /usr/lib/firefox/firefox -contentproc -childID 6 -isForBrowser -prefsLen 56 -prefMapSize 545346 -parentBuildID 20200818235255 -appdir /usr/lib/firefox/browser 44 true tab
tf       22918 22624  0 Aug30 pts/2    00:01:25 /usr/lib/firefox/firefox -contentproc -childID 7 -isForBrowser -prefsLen 56 -prefMapSize 545346 -parentBuildID 20200818235255 -appdir /usr/lib/firefox/browser 44 true tab
tf       22949 22624  0 Aug30 pts/2    00:05:37 /usr/lib/firefox/firefox -contentproc -childID 8 -isForBrowser -prefsLen 56 -prefMapSize 545346 -parentBuildID 20200818235255 -appdir /usr/lib/firefox/browser 44 true tab
tf       23063 22624  1 Aug30 pts/2    00:30:57 /usr/lib/firefox/firefox -contentproc -childID 9 -isForBrowser -prefsLen 6527 -prefMapSize 545346 -parentBuildID 20200818235255 -appdir /usr/lib/firefox/browser 44 true tab
tf       29618 22624  0 Aug30 pts/2    00:00:39 /usr/lib/firefox/firefox -contentproc -childID 10 -isForBrowser -prefsLen 7271 -prefMapSize 545346 -parentBuildID 20200818235255 -appdir /usr/lib/firefox/browser 44 true tab

```
But top does show MainThread and PaintThread --- hum.  People should be shot over doing things like that. Obfuscation of process names cannot be tolerated.

> **maglin2 said:**
> I agree - though 20.04 does run really pretty well. More significantly  it's for my wife, and it is, I think, the most attractive and user  friendly Ubuntu interface for a novice (and frankly disinterested) user.  When it doesn't freeze she's delighted with it! 5 year support is  another plus  - reduces the change frequency. Her only OS experience  before this was a chromebook - which was simplicity itself and totally  bombproof, but is now AUE.  May yet have to buy another though.
I might try her with Xubuntu or Lubuntu if I do a reinstall.

Everyone has different tastes.  Ubuntu-Mate is nice.  I'm an LTS-only user and the Gnome3 variant is the only DE w/ 5 yrs of support. There are lots of other DEs, just with 3 yrs.  I don't use any DE - fvwm is my WM, but it has been crazy stable for about 20 yrs and highly customizable.  

Just to change the GUI, there's no need to reinstall the OS. The GUI is NOT the OS, it is just another program or suite of programs.  Installing a different DE is 1 apt install, logout, pick a different DE from the "gear" icon, then login.  The trick is to use a different userid for each DE so settings don't conflict between DEs that are using the same underlying support libraries.  So, XFCE and Mate and Cinnamon are all gnome2, so using a different userid for each why you try them out would be smart. Actually, I'd do that with any Gnome-base DE.  For KDE, LXQT also uses the same Qt libraries, so I'd use a new userid while testing each of those.  The safe answer is to always create a new userid for testing any DE ...  but if you move to just MW-based GUIs, say openbox or fvwm, then we don't need to worry about settings clobbering each other.

Skip this story:
I have 2 Chromebooks. Only used ChromeOS for a few weeks before wiping. I found it much to frustrating to have nearly an ultrabook, dumbed down to the point that it couldn't connect to any of my network storage AND Google would push patches with no way to stop them.  At the time, I was doing lots of international travel. Got a new OS the night before a long trip to Asia. Opened the chromebook in the airport and it was bricked.  I wasn't going to have internet for a few weeks, so google totally screwed me.  Canonical is doing that with snaps, though the keep 3 copies around for each snap package to mitigate that ... but on a system with 16G of total storage, snaps that are 900MB in size for a 32MB program are just too wasteful to be considered at all.  Snaps are supposed to make life easier and more secure. They've failed at both for my needs.  Sadly, a few programs I want and one that I must, must, have are only available as snaps now, so I can't purge them and just not use it.

I think the best answer right now based on the problem description is to increase the swap to 4.1G.  That would really be disable swap and create a new swap of the correct size, then enable it.  **mkswap** is the command to format a block device as swap. In theory, with a 1G swap, you could add 3G more in a separate file, then add that using mkswap, edit the fstab, and sudo swapon -a, but who wants to have 2 swap devices/files to manage. Also, if you have a spinning HDD internal, I'd put the swap on that, not the SSD.  Remember, the goal of swap is to let the user "feel" the system getting slower so she can take action to close extra programs.

---

### Post by maglin2 on 2020-09-01
The laptop has one SSD only (it's only 11", so there's not a lot of room). Anyway, I suspect there is no chance that the user would treat a longer 'system slowing' symptom from having more swap as anything other than a prompt to press keys repeatedly/more vigorously.

The other suggestion of a different user ID running a different DE has more promise for diagnosis I think. 

I'll install panel widgets showing cpu temps, RAM use and swap use. Then a screen freeze will at least leave a visible signal of any prior overheating or out of memory.

(I'll look into conky on vanilla Ubuntu first though - it's not something I've ever used, but I see there's a whopping thread about it, so a lot of folks must).

I ran the short disk test with smartctl - it found no errors.

Thanks again to all.

---

### Post by maglin2 on 2020-09-01
> **CatKiller said:**
> Conky is good for that. It can query all kinds of stuff (or run arbitrary things) and draws the result onto the desktop. The things you're interested in are easily accomplished with conky objects.

Can conky display be configured to be always on top of other windows and fully transparent (other than text)?
Thanks

---

### Post by CatKiller on 2020-09-01
> **maglin2 said:**
> Can conky display be configured to be always on top of other windows and fully transparent (other than text)?
Thanks

Yes. Giving it the **above** window hint (rather than below) will put it on top of all other windows. Transparent with visible text is the way that most people have it, I think.

---

### Post by maglin2 on 2020-09-02
Thanks.
Conky works, but I think looks really messy on top of a scrolling browser window.

I've gone for a panel applet approach using gnome flashback for now. Temperatures, cpu load, RAM and swap use are all now displayed in the panel. If there's another freeze I'll hopefully get a bit more of a clue as to what's going on.

---

### Post by dragonfly41 on 2020-09-02
There is also GKrellM System Monitor to watch those parameters.

---

### Post by CatKiller on 2020-09-02
> **maglin2 said:**
> Thanks.
Conky works, but I think looks really messy on top of a scrolling browser window.

Well, putting it in top was your idea.

I have mine drawn on the edge of my desktop, rarely covered because widescreen monitor.

---

### Post by maglin2 on 2020-09-02
> **CatKiller said:**
> Well, putting it in top was your idea.

I have mine drawn on the edge of my desktop, rarely covered because widescreen monitor.

Fair enough - but when you've only got an 11" laptop and old eyes display space is at a premium!

---

### Post by dragonfly41 on 2020-09-02
> [COLOR=#000000]display space is at a premium![/COLOR]

Extend your display space by using Virtual Workspaces.
I use a docklet in Docky for switching.

---

### Post by maglin2 on 2020-09-02
> **dragonfly41 said:**
> Extend your display space by using Virtual Workspaces.
I use a docklet in Docky for switching.

Would that help? My problem is that when the system freezes no input works - so process information displayed in a space not visible at the time of the freeze will remain forever invisible.

---

### Post by dragonfly41 on 2020-09-02
You can dump the GKrellM output at intervals to refer to when you resume normal working.

---

### Post by maglin2 on 2020-09-02
> **dragonfly41 said:**
> You can dump the GKrellM output at intervals to refer to when you resume normal working.

I that functionality built-in, or would it need to be done by scripting?

---

### Post by dragonfly41 on 2020-09-02
Options are documented here.

[https://wiki.gentoo.org/wiki/GKrellM](https://wiki.gentoo.org/wiki/GKrellM)

If you install Synaptic Package Manager and search gkrell you see a full list of optional plugins.


There is also a daemon (without GUI) which runs in background for remote monitoring.

See gkrellm (gui) vs. gkrellmd (daemon).


This script takes a snapshot

[https://nmap.org/nsedoc/scripts/gkrellm-info.html](https://nmap.org/nsedoc/scripts/gkrellm-info.html)

This could be run as a cronjob.

[P.S.] In GKrellM configuration GUI (right click on popup window) each plugin parameter can trigger an Alert command so you can run commands if say temperature level is exceeded.

---

### Post by maglin2 on 2020-09-02
Thanks for that. It would be quite a learning exercise for me, but in the current situation I'm not exactly plagued by distractions.

---

### Post by dragonfly41 on 2020-09-02
Having suggested the above I'm not sure if this will detect cause of your freeze. You could try other experiments such as creating a fresh logon account (guest) to see if freezes still occur.  Then there are extensions in browsers to disable. There is also hardware acceleration .. and so the list of possibilities/theories grows.  A systematic process of elimination is needed. When last I encountered freezes on an old laptop I followed lots of ideas such as removing memory cards and cleaning board edges with a clean rubber then carefully replacing.


**[P.S.] **Throwing into the ring another idea.
Install Stacer from here.
[https://github.com/oguzhaninan/Stacer](https://github.com/oguzhaninan/Stacer)

[COLOR=#24292E][FONT=SFMono-Regular]sudo add-apt-repository <add repository path here .. [/FONT][/COLOR][COLOR=#ff0000][FONT=SFMono-Regular]pasting it here creates this! ppa:oguzhaninan/stacer -[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular] > 
[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]sudo apt-get update
[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]sudo apt-get install stacer -y

[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]Then look at the Stacer Resources dashboard to monitor resource peaks.
[/FONT][/COLOR]
It* might* offer some clues.

---

### Post by maglin2 on 2020-09-03
I agree that diagnosing/remedying this might be a slow process. The freeze has only been happening about once a month, so opportunities to test theories are pretty limited too.

I've tried stacer before, but found then that it was the biggest consumer of cpu on the system. Maybe it's improved.

I have tested storage, I'm about to run a RAM test, and I have panel displays of cpu load, RAM, swap, all temperatures and battery voltage. 

Hopefully I might spot something between those and the logs come the next freeze to give me a clue to follow.

This is a low energy cpu. It's not Bay Trail, but I have been wondering if cpu idle.max cstate might be an issue.

[https://easylinuxtipsproject.blogspot.com/p/bugs.html#ID25](https://easylinuxtipsproject.blogspot.com/p/bugs.html#ID25)

[https://bbs.archlinux.org/viewtopic.php?id=236686](https://bbs.archlinux.org/viewtopic.php?id=236686)

Currently it's 9.
I'm a bit reluctant to play with it, since battery life was one of the drivers for getting the machine.

---

### Post by dragonfly41 on 2020-09-03
One final shot .. install **petit** to try to make sense out of accumulated log files up to the point of freeze.
Another log search tool is **glogg**.

---

### Post by maglin2 on 2020-11-28
Just some info for all those who helped. 
I installed Mate 20.04, festooned the top panel with real time monitoring of pretty much everything monitorable - and it hasn't frozen since!
Which is a result of sorts  in itself I suppose.

---

### Post by ajgreeny on 2020-11-28
> **maglin2 said:**
> Just some info for all those who helped. 
I installed Mate 20.04, festooned the top panel with real time monitoring of pretty much everything monitorable - and it hasn't frozen since!
Which is a result of sorts  in itself I suppose.
That seems to point to the gnome DE being at least part of the problem, maybe due to memory problems of some sort, gnome generally requiring more RAM to run smoothly than Mate though your inxi output in post #5 .does not support this theory.
Something else related to gnome?  I haven't the faintest idea as I do not use it.

---


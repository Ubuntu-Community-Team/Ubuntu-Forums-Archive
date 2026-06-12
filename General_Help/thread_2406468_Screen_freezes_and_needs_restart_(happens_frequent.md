---
title: "Screen freezes and needs restart (happens frequently)"
date: 2018-11-21
forum: General Help
---

### Post by jonathan81998 on 2018-11-21
Hello all,


I need support here. I have had this problem regularly for like the last 6 months.


I am running Ubuntu 18.10 (I upgraded 1 month ago from 18.04 and had the same issue with 18.04). Quite often (multiple times per day), the screen freezes and nothing responds anymore. I try CTRL-ALT-F1 thinking that it's only the GUI, but that does not work. I have to reboot my computer.
I don't know if it is software or hardware. Would you have some way to understand that?
I thought that it could be from processes that use a lot of cpu, like dropbox or chrome, but even with those closed, it sometimes happens to me.
I also thought that it could come from the graphic card driver, but I tried using X.Org X server (normally I use NVIDIA driver), and it happened also.
For info, it only happens when my session is locked and I don't do anything with it.


I give you some more info about my machine below. I would be grateful if someone could help me figure this out.


Info about my machine from neofetch:
```
$ neofetch




--------------------------- 
OS: Ubuntu 18.10 x86_64 
Kernel: 4.18.0-10-generic 
Uptime: 38 mins 
Packages: 2987 (dpkg), 3 (snap) 
Shell: bash 4.4.19 
Resolution: 3440x1440 
DE: GNOME 3.30.1 
WM: GNOME Shell 
WM Theme: Adwaita 
Theme: Yaru [GTK2/3] 
Icons: Yaru [GTK2/3] 
Terminal: terminator 
CPU: Intel i7-6700K (8) @ 4.200GHz 
GPU: NVIDIA GeForce GTX 1070 
Memory: 4518MiB / 15981MiB 

```


Info about my screen:
```
$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: GP104 [GeForce GTX 1070]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:125 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff

```


The last lines in syslog before a freeze. After the last line here, there is a line of funny characters just at the time of the freeze, but they don't display here. Freeze happened at 12:11 in the present case. Could it have something to do with the "cannot get renderprocesshost" error?
```

Nov 21 12:00:43 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120043.469336:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:01:43 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120143.772098:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:02:44 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120244.107427:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:03:44 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120344.407186:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:04:44 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120444.734684:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:04:57 jon-System-Product-Name systemd[1]: Started Run anacron jobs.
Nov 21 12:04:57 jon-System-Product-Name anacron[7050]: Anacron 2.3 started on 2018-11-21
Nov 21 12:04:57 jon-System-Product-Name anacron[7050]: Normal exit (0 jobs run)
Nov 21 12:05:19 jon-System-Product-Name NetworkManager[1024]: <info>  [1542798319.7679] manager: NetworkManager state is now CONNECTED_SITE
Nov 21 12:05:19 jon-System-Product-Name dbus-daemon[1017]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.8' (uid=0 pid=1024 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Nov 21 12:05:19 jon-System-Product-Name systemd[1]: Starting Network Manager Script Dispatcher Service...
Nov 21 12:05:19 jon-System-Product-Name dbus-daemon[1017]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 21 12:05:19 jon-System-Product-Name nm-dispatcher: req:1 'connectivity-change': new request (1 scripts)
Nov 21 12:05:19 jon-System-Product-Name systemd[1]: Started Network Manager Script Dispatcher Service.
Nov 21 12:05:19 jon-System-Product-Name nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
Nov 21 12:05:20 jon-System-Product-Name NetworkManager[1024]: <info>  [1542798320.2500] manager: NetworkManager state is now CONNECTED_GLOBAL
Nov 21 12:05:20 jon-System-Product-Name nm-dispatcher: req:2 'connectivity-change': new request (1 scripts)
Nov 21 12:05:20 jon-System-Product-Name nm-dispatcher: req:2 'connectivity-change': start running ordered scripts...
Nov 21 12:05:45 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120545.045078:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:06:45 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120645.360971:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:07:45 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120745.716607:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:08:46 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120846.094004:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Nov 21 12:09:46 jon-System-Product-Name org.gnome.Shell.desktop[3216]: [3727:3727:1121/120946.398235:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost





```


Thank you very much for your help.

---

### Post by daredyoshi on 2018-12-31
Heya! I've been having the same problem since november on CentOs 7. 

```
Dec 31 09:52:38 baboonbrain pulseaudio[3169]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Dec 31 09:52:48 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/095248.844489:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 09:54:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/095440.664516:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 09:56:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/095640.700672:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 09:58:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/095840.648421:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:00:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/100040.566658:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:02:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/100240.676048:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:04:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/100440.643987:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:06:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/100640.653228:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:08:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/100840.675312:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:10:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/101040.590055:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:12:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/101240.674327:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:14:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/101440.697470:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:16:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/101640.704442:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:18:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/101840.597092:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:20:38 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/102038.266563:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:21:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/102140.665902:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:23:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/102340.693401:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:25:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/102540.724067:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:27:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/102740.706888:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:29:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/102940.700327:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:31:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/103140.627141:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:33:49 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/103349.582302:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:35:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/103540.686194:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:36:24 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/103624.768281:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:37:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/103740.682271:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:39:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/103940.717246:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:41:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/104140.602969:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:43:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/104340.749790:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:45:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/104540.635340:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:47:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/104740.590502:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:49:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/104940.695002:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:51:40 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/105140.767948:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost
Dec 31 10:52:14 baboonbrain evolution-sourc[3249]: secret_service_search_sync: must specify at least one attribute to match
Dec 31 10:52:15 baboonbrain gnome-keyring-daemon[2899]: asked to register item /org/freedesktop/secrets/collection/login/1, but it's already registered
Dec 31 10:52:16 baboonbrain evolution-calen[3996]: ecb_gtasks_start_update: assertion 'cancellable != NULL' failed
Dec 31 10:53:41 baboonbrain google-chrome.desktop[4301]: [4301:4301:1231/105341.312785:ERROR:media_internals.cc(104)] Cannot get RenderProcessHost

```
It only happens when my gpu starts idleling. I also have Nvidia (GTX 970), and my theory is that it has something to do with the driver like you said. Maybe it's hardware related? Have you figured out any way to get around this?

---

### Post by Autodave on 2018-12-31
First off, daredyoshi, please start your own thread.  What fixes your system is quite likely to fix the original poster's.  Plus, you are running a different desktop.

For both of you, though, try running a RAM test.  Failing RAM will cause that condition.  Overheating is another possible cause.  Are fans and the CPU heatsink clean?  Are fans operating?  Leaving the side off of the box will let a lot of extra air into the system: you may try that to see if it helps.  If it does, you will at least know then that overheating is the culprit and can proceed from there.

---


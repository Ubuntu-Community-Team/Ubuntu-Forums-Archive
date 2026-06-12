---
title: "*buntu 8.04: dd running at startup?"
date: 2013-10-29
forum: General Help
---

### Post by TheDoktor on 2013-10-29
[FONT=verdana]Hello folks, I have recently discovered, while running XFCE Process Manager, that the famous-infamous "***dd***" program is running (at every boot, yeah) ; I can't imagine which program is launching it and for which reason, however, I'm stopping it with "[FONT=courier new]sudo kill xxxx[/FONT]" each time I reboot my PC (xxxx is the relevant process id-number, as seen in process manager).
So what is that, malware activity? Someone/something trying to wipe my hard drive? [/FONT]:confused::confused::confused::confused::confused:


[FONT=verdana] About my PC: I am using these days a somewhat-very-personal-flavor of XFCE running  on top of Kubuntu 8.04 Hardy Heron, with a  simple look and  extremely personalized panels; this machine is based on an old Sempron  3000+, but I can ensure you that it runs fast, I use it for basic  desktop activity and multimedia (including music editing with audacity).[/FONT]:KS

---

### Post by The Cog on 2013-10-29
The command 
```
pstree -lU
``` might help. dd's command line arguments will give you an idea what it's doing and the tree will show you what launched it.

---

### Post by mörgæs on 2013-10-29
Thought 8.04 might be fast it's not secure. As it has been out of support for many years it's likely that black hats have found security holes which will not be fixed. 

Have you thought of a fresh install of 13.10?

---

### Post by TheDoktor on 2013-10-30
> **mörgæs said:**
> Thought 8.04 might be fast it's not secure. As it has been out of support for many years it's likely that black hats have found security holes which will not be fixed. 

Have you thought of a fresh install of 13.10?

true, but the server edition was supported up to last April (if I am not wrong), and many files at *[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) hardy-updates *look recent to me. 
I am a freelance tech support and I need to experiment with everything I can, both software (OSes) and hardware equipment, I think I wll keep using this system for some tasks in my laboratory, and keep it away from the net.
I don't appreciate Unity, Gnome3 and KDE4, these desktop environments and those from MS (WIndoz V*sta onward), give me strong headaches due to their colours (well, it's even worst than this, but I am keeping private my own health issues);
 I still like the Ubuntu family, I've tried Xubuntu and Lubuntu 13.04, both are very fine, though I like to grab the original XFCE and LXDE files and make my own desktop :) I didn't try anything 13.10, yet. I'll let you know.

---

### Post by TheDoktor on 2013-10-30
> **The Cog said:**
> The command 
```
pstree -lU
``` might help. dd's command line arguments will give you an idea what it's doing and the tree will show you what launched it.


Thank you :) , I tried it yesterday, but I got no clue yet, I will try it again later today, after next reboot. :P

---

### Post by TheDoktor on 2013-11-01
> **The Cog said:**
> The command 
```
pstree -lU
``` might help. dd's command line arguments will give you an idea what it's doing and the tree will show you what launched it.

After typing pstree -lU  in terminal, this is what I got:

```
user@computer:~$ pstree -lU
init&#9472;&#9516;&#9472;NetworkManager
     &#9500;&#9472;NetworkManagerD
     &#9500;&#9472;Thunar
     &#9500;&#9472;acpid
     &#9500;&#9472;anacron
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;61*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dcopserver
     &#9500;&#9472;dd
     &#9500;&#9472;debtorrent-clie
     &#9500;&#9472;dhcdbd
     &#9500;&#9472;dirmngr
     &#9500;&#9472;gam_server
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-volume-ma
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9492;&#9472;hald-addon-inpu
     &#9500;&#9472;hcid&#9472;&#9472;&#9472;2*[bluetoothd-serv]
     &#9500;&#9472;jockey-gtk
     &#9500;&#9472;kded
     &#9500;&#9472;kdeinit&#9472;&#9472;&#9472;klauncher
     &#9500;&#9472;kdm&#9472;&#9516;&#9472;Xorg
     &#9474;     &#9492;&#9472;kdm&#9472;&#9472;&#9472;sh&#9472;&#9516;&#9472;seahorse-agent
     &#9474;                &#9500;&#9472;ssh-agent
     &#9474;                &#9492;&#9472;xfce4-session&#9472;&#9472;&#9472;{xfce4-session}
     &#9500;&#9472;klogd
     &#9500;&#9472;netdaemon
     &#9500;&#9472;nm-applet
     &#9500;&#9472;ntpd
     &#9500;&#9472;syslogd
     &#9500;&#9472;system-tools-ba
     &#9500;&#9472;udevd
     &#9500;&#9472;update-notifier
     &#9500;&#9472;winbindd&#9472;&#9472;&#9472;winbindd
     &#9500;&#9472;xfce-mcs-manage
     &#9500;&#9472;xfce4-panel&#9472;&#9516;&#9472;thunar-tpa
     &#9474;             &#9500;&#9472;xfce4-clipman-p
     &#9474;             &#9500;&#9472;xfce4-cpufreq-p
     &#9474;             &#9500;&#9472;xfce4-cpugraph-
     &#9474;             &#9500;&#9472;xfce4-menu-plug
     &#9474;             &#9500;&#9472;2*[xfce4-mixer-plu]
     &#9474;             &#9500;&#9472;xfce4-mount-plu
     &#9474;             &#9500;&#9472;xfce4-netload-p
     &#9474;             &#9492;&#9472;xfce4-places-pl
     &#9500;&#9472;xfce4-taskmanag
     &#9500;&#9472;xfdesktop
     &#9492;&#9472;xfwm4
```


I've decided to rename dd into dd_  ,  this is turning effective, but it's just a temporary solution in my opinion.

---

### Post by The Cog on 2013-11-02
Well that listing wasn't useful. I had it in mind that '-l' would list the command line arguments to dd. Silly me.
Please can you do
```
ps -ef | grep dd
```
next time you boot, so we can see what dd is actually doing. I really doubt that it's a virus though.

---

### Post by TheDoktor on 2013-11-05
> **The Cog said:**
> Well that listing wasn't useful. I had it in mind that '-l' would list the command line arguments to dd. Silly me.
Please can you do
```
ps -ef | grep dd
```
next time you boot, so we can see what dd is actually doing. I really doubt that it's a virus though.



):P):P):P
that's the output:

```
user@computer:~$ sudo ps -ef | grep dd
[sudo] password for user:
root         2     0  0 19:06 ?        00:00:00 [kthreadd]
root      5262     1  0 19:09 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v                                                             ar/run/klogd/kmsg
root      5535     1  0 19:09 ?        00:00:00 /usr/sbin/winbindd
root      5586  5535  0 19:09 ?        00:00:00 /usr/sbin/winbindd
root      5709  5685  0 19:09 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
109       5710  5685  0 19:09 ?        00:00:00 hald-addon-acpi: listening on ac                                                             pid socket /var/run/acpid.socket
root      5713  5685  0 19:09 ?        00:00:00 hald-addon-input: Listening on /                                                             dev/input/event1 /dev/input/event4 /dev/input/event5
root      5729  5685  0 19:10 ?        00:00:00 hald-addon-storage: polling /dev                                                             /scd0 (every 2 sec)
user      6370  6369  0 19:11 ?        00:00:00 /bin/sh -c ksysguardd
user      6371  6370  1 19:11 ?        00:00:06 ksysguardd
user      6814  6797  0 19:21 pts/3    00:00:00 grep dd
```

---

### Post by TheDoktor on 2013-11-05
thanks to the info provided by the [FONT=courier new]grep [/FONT]command, I could do a more effective search, and I've found this page that seems to answer to my question:
[http://fixunix.com/ubuntu/551193-why-there-dd-process-running-daemon.html](http://fixunix.com/ubuntu/551193-why-there-dd-process-running-daemon.html)

---

### Post by mörgæs on 2013-11-05
Good. If this solves your problem please mark the thread so.

---

### Post by TheDoktor on 2013-11-05
> **mörgæs said:**
> Good. If this solves your problem please mark the thread so.
  

Honestly, I don't feel like it is solved, further searches made me suspicious, I can't see any good reason behind such kernel's behaviour.

---

### Post by TheDoktor on 2013-12-17
I have some more clues about this issue, I will post 2 screen captions as soon as I learn how to upload here :)

---


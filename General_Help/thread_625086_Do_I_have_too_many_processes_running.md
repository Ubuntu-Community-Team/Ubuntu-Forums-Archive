---
title: "Do I have too many processes running??"
date: 2007-11-27
forum: General Help
---

### Post by herbster on 2007-11-27
This is out of simple curiousity. Now my normal running programs are: FF (1-2 windows), Opera, XChat, bunch of nautilus file browsers, 1-3 gnome-terminals, Terminal Server Client and 2-3 OO spreadsheets.

```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Nov18 ?        00:00:03 /sbin/init
root         2     0  0 Nov18 ?        00:00:00 [kthreadd]
root         3     2  0 Nov18 ?        00:00:00 [migration/0]
root         4     2  0 Nov18 ?        00:00:11 [ksoftirqd/0]
root         5     2  0 Nov18 ?        00:00:00 [watchdog/0]
root         6     2  0 Nov18 ?        00:00:00 [migration/1]
root         7     2  0 Nov18 ?        00:00:03 [ksoftirqd/1]
root         8     2  0 Nov18 ?        00:00:00 [watchdog/1]
root         9     2  0 Nov18 ?        00:00:04 [events/0]
root        10     2  0 Nov18 ?        00:00:00 [events/1]
root        11     2  0 Nov18 ?        00:00:00 [khelper]
root        31     2  0 Nov18 ?        00:00:00 [kblockd/0]
root        32     2  0 Nov18 ?        00:00:00 [kblockd/1]
root        33     2  0 Nov18 ?        00:00:00 [kacpid]
root        34     2  0 Nov18 ?        00:00:00 [kacpi_notify]
root       123     2  0 Nov18 ?        00:00:00 [kseriod]
root       143     2  0 Nov18 ?        00:00:39 [pdflush]
root       144     2  0 Nov18 ?        00:03:42 [kswapd0]
root       195     2  0 Nov18 ?        00:00:00 [aio/0]
root       196     2  0 Nov18 ?        00:00:00 [aio/1]
root      2039     2  0 Nov18 ?        00:00:00 [ata/0]
root      2040     2  0 Nov18 ?        00:00:00 [ata/1]
root      2041     2  0 Nov18 ?        00:00:00 [ata_aux]
root      2044     2  0 Nov18 ?        00:00:00 [scsi_eh_0]
root      2045     2  0 Nov18 ?        00:00:00 [scsi_eh_1]
root      2049     2  0 Nov18 ?        00:00:00 [ksuspend_usbd]
root      2050     2  0 Nov18 ?        00:00:00 [khubd]
www-data  2086  5683  0 Nov26 ?        00:00:00 /usr/sbin/apache2 -k start
root      2585     2  0 Nov18 ?        00:00:10 [kjournald]
bobby     2770 19936  0 15:57 ?        00:00:01 rdesktop -T192.168.1.105 - Termi
root      2791     1  0 Nov18 ?        00:00:03 /sbin/udevd --daemon
bobby     3736  5810  0 Nov26 ?        00:00:42 xchat
bobby     3778  5810  0 Nov25 ?        00:02:06 /usr/bin/python -OO /usr/bin/pyp
root      3783     2  0 Nov18 ?        00:00:00 [kpsmoused]
bobby     3835 10563  0 16:06 pts/2    00:00:00 bash
root      4018     2  0 Nov18 ?        00:00:00 [kgameportd]
bobby     4044  5810  0 Nov25 ?        00:01:15 gimp
bobby     4047  4044  0 Nov25 ?        00:00:00 /usr/lib/gimp/2.0/plug-ins/scrip
root      4296     2  0 Nov18 ?        00:00:19 [kjournald]
root      4297     2  0 Nov18 ?        00:00:09 [kjournald]
root      4298     2  0 Nov18 ?        00:00:26 [kjournald]
root      4299     2  0 Nov18 ?        00:00:00 [kjournald]
bobby     4545 10563  4 16:13 pts/3    00:00:00 bash
root      4564     1  0 Nov18 tty4     00:00:00 /sbin/getty 38400 tty4
root      4565     1  0 Nov18 tty5     00:00:00 /sbin/getty 38400 tty5
root      4567     1  0 Nov18 tty2     00:00:00 /sbin/getty 38400 tty2
root      4569     1  0 Nov18 tty3     00:00:00 /sbin/getty 38400 tty3
root      4571     1  0 Nov18 tty1     00:00:00 /sbin/getty 38400 tty1
root      4572     1  0 Nov18 tty6     00:00:00 /sbin/getty 38400 tty6
bobby     4577  4545  0 16:13 pts/3    00:00:00 ps -ef
root      4758     1  0 Nov18 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      4804     2  0 Nov18 ?        00:00:00 [kondemand/0]
root      4805     2  0 Nov18 ?        00:00:00 [kondemand/1]
www-data  4853  5683  0 Nov25 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  4854  5683  0 Nov25 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  4855  5683  0 Nov25 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  4856  5683  0 Nov25 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  4857  5683  0 Nov25 ?        00:00:00 /usr/sbin/apache2 -k start
syslog    4883     1  0 Nov18 ?        00:00:01 /sbin/syslogd -u syslog
root      4937     1  0 Nov18 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      4939     1  0 Nov18 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
103       4960     1  0 Nov18 ?        00:00:11 /usr/bin/dbus-daemon --system
root      4976     1  0 Nov18 ?        00:00:00 /usr/sbin/NetworkManager --pid-f
root      4990     1  0 Nov18 ?        00:00:00 /usr/sbin/NetworkManagerDispatch
root      5003     1  0 Nov18 ?        00:00:00 /usr/bin/system-tools-backends
root      5004  5003  0 Nov18 ?        00:00:00 dbus-daemon --session --print-ad
107       5023     1  0 Nov18 ?        00:00:16 /usr/sbin/hald
root      5024  5023  0 Nov18 ?        00:00:00 hald-runner
107       5078  5024  0 Nov18 ?        00:00:04 hald-addon-keyboard: listening o
107       5081  5024  0 Nov18 ?        00:00:00 hald-addon-keyboard: listening o
107       5082  5024  0 Nov18 ?        00:00:00 hald-addon-keyboard: listening o
107       5083  5024  0 Nov18 ?        00:00:00 hald-addon-keyboard: listening o
root      5088     1  0 Nov18 ?        00:00:00 /usr/sbin/sshd
107       5093  5024  0 Nov18 ?        00:00:00 hald-addon-acpi: listening on ac
root      5140     1  0 Nov18 ?        00:00:00 /usr/sbin/cupsd
root      5228     1  0 Nov18 ?        00:00:01 /usr/sbin/hddtemp -d -l 127.0.0.
root      5301     1  0 Nov18 ?        00:00:00 /usr/sbin/console-kit-daemon
avahi     5404     1  0 Nov18 ?        00:00:00 avahi-daemon: running [bobby-dab
avahi     5405  5404  0 Nov18 ?        00:00:00 avahi-daemon: chroot helper
bobby     5413     1  0 Nov19 ?        01:56:20 amarokapp -m
root      5419     1  0 Nov18 ?        00:00:00 /usr/sbin/dhcdbd --system
bobby     5434  5413  0 Nov19 ?        00:00:00 ruby /usr/share/apps/amarok/scri
bobby     5435  5413  0 Nov19 ?        00:18:06 ruby /usr/share/apps/amarok/scri
107       5445  5024  0 Nov18 ?        00:00:23 hald-addon-storage: polling /dev
107       5451  5024  0 Nov18 ?        00:00:06 hald-addon-storage: polling /dev
root      5463     2  0 Nov18 ?        00:00:00 [krfcommd]
root      5504     1  0 Nov18 ?        00:00:00 /usr/sbin/gdm
root      5507  5504  0 Nov18 ?        00:00:07 /usr/sbin/gdm
root      5510  5507  5 Nov18 tty7     12:01:57 /usr/bin/X :0 -br -audit 0 -auth
dhcp      5533  5419  0 Nov18 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/d
daemon    5589     1  0 Nov18 ?        00:00:00 /usr/sbin/atd
root      5604     1  0 Nov18 ?        00:00:01 /usr/sbin/cron
root      5683     1  0 Nov18 ?        00:00:00 /usr/sbin/apache2 -k start
bobby     5807     1  0 Nov18 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d
bobby     5810  5507  0 Nov18 ?        00:03:22 /usr/bin/openbox --sm-save-file
bobby     5853  5810  0 Nov18 ?        00:00:01 /usr/bin/ssh-agent /usr/bin/dbus
bobby     5856     1  0 Nov18 ?        00:00:00 /usr/bin/dbus-launch --exit-with
bobby     5857     1  0 Nov18 ?        00:00:14 /usr/bin/dbus-daemon --fork --pr
bobby     5873  5810  0 Nov18 ?        00:02:27 gnome-settings-daemon
root      5883     1  0 Nov18 ?        00:00:00 start_kdeinit --new-startup +kcm
bobby     5887     1  0 Nov18 ?        00:00:06 /usr/lib/libgconf2-4/gconfd-2 6
bobby     5888     1  0 Nov18 ?        00:00:00 kdeinit Running...             
bobby     5895     1  0 Nov18 ?        00:00:05 gnome-power-manager
bobby     5899     1  0 Nov18 ?        00:00:01 dcopserver [kdeinit] --nosid   
bobby     5902     1  0 Nov18 ?        00:26:02 gnome-screensaver
bobby     5903  5888  0 Nov18 ?        00:00:00 klauncher [kdeinit] --new-startu
bobby     5906     1  0 Nov18 ?        00:01:09 kded [kdeinit] --new-startup   
root      6993     2  0 Nov24 ?        00:00:00 [scsi_eh_5]
root      6994     2  0 Nov24 ?        00:00:02 [usb-storage]
bobby     7027     1  0 Nov18 ?        00:47:27 /usr/lib/gnome-vfs-2.0/gnome-vfs
bobby     7244     1  0 Nov19 ?        00:00:10 kio_uiserver [kdeinit]         
bobby     8416  5810  0 Nov18 ?        00:00:23 nvidia-settings
bobby     8501     1  0 Nov19 ?        00:00:07 knotify [kdeinit]              
bobby     9967     1  0 Nov22 ?        00:00:34 /usr/lib/notification-daemon/not
bobby    10243     1  0 Nov26 ?        00:01:28 /usr/bin/trackerd
root     10347     2  0 13:01 ?        00:00:00 [scsi_eh_6]
root     10348     2  0 13:01 ?        00:00:00 [usb-storage]
107      10438  5024  0 13:01 ?        00:00:00 hald-addon-storage: polling /dev
107      10440  5024  0 13:01 ?        00:00:00 hald-addon-storage: polling /dev
107      10442  5024  0 13:01 ?        00:00:00 hald-addon-storage: polling /dev
107      10444  5024  0 13:01 ?        00:00:00 hald-addon-storage: polling /dev
bobby    10563  5810  0 13:02 ?        00:00:02 gnome-terminal
bobby    10566 10563  0 13:02 ?        00:00:00 gnome-pty-helper
bobby    10567 10563  0 13:02 pts/0    00:00:00 bash
bobby    12526  5810  0 13:21 ?        00:00:00 /bin/sh /usr/bin/firefox
bobby    12538 12526  0 13:21 ?        00:00:00 /bin/sh /usr/lib/firefox/run-moz
bobby    12542 12538 11 13:21 ?        00:19:43 /usr/lib/firefox/firefox-bin
bobby    12595  5888  0 Nov22 ?        00:00:00 kio_file [kdeinit] file /tmp/kso
bobby    13224  5810  1 13:28 ?        00:01:54 /usr/lib/opera/9.24-20071015.6/o
bobby    16957  5810  0 Nov20 ?        00:00:10 obconf
bobby    17774  5810  0 Nov20 ?        00:00:20 /usr/bin/python /usr/bin/obmenu
bobby    19936  5810  0 Nov18 ?        00:00:31 tsclient
bobby    21003     1  0 Nov21 ?        00:09:26 conky
root     21540     2  0 Nov19 ?        00:00:12 [pdflush]
bobby    22509  5810 14 Nov26 ?        03:19:02 gnome-system-monitor
bobby    23845     1  0 Nov26 ?        00:00:00 gnome-obex-server
bobby    24379     1  0 Nov26 ?        00:00:00 /usr/lib/bonobo-activation/bonob
root     24502     1  0 Nov26 ?        00:00:00 /usr/sbin/hcid -x -s
root     24510 24502  0 Nov26 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-se
root     24511 24502  0 Nov26 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-se
bobby    24888  5810  0 Nov26 ?        00:03:21 nautilus --no-desktop /home/bobb
bobby    24893     1  0 Nov26 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp
bobby    26933     1  0 Nov26 ?        00:00:00 /usr/bin/gpilotd --oaf-activate-
root     28635     1  0 Nov18 ?        00:00:00 /usr/bin/timidity -Os -iAD
bobby    28750     1  0 Nov20 ?        00:00:00 /bin/sh /usr/lib/openoffice/prog
bobby    28776 28750  0 Nov20 ?        00:02:26 /usr/lib/openoffice/program/soff
bobby:~$
```

My conky shows between 230-246 processes running on average. Is it fine or can I trim it down?

---

### Post by zach12 on 2007-11-27
If you have a lot of Ram it's fine

---

### Post by herbster on 2007-11-27
Well, I have 1.2gb ram and a 4gb swap partition, but with what I have above running my memory is at 61% usage.

---

### Post by sethvath on 2007-11-28
If you dont experience any general slowness of the system it should be fine. 

Just for comparison, I have 192 processes running, 21% mem usage. System specs+background: 4gb ram, 2gb swap, FF with 14 tabs, xterm, ktorrent, amarok

Most days I run more programs than this and no problems with gutsy. On windows and mac osx, I'll start experiencing lags in system responsiveness

---

### Post by herbster on 2007-11-28
I get quite some lag in FF when opening tabs and switching while another is loading. Is this just FF or somethin' else? Especially pages like digg.com.

---

### Post by -grubby on 2007-11-28
you could try disabling unnecessary services...for example i disabled tracker and bluetooth because I don't use them

---

### Post by teryowen on 2007-11-28
I seem to have many things running also, not really slowing it down but i want to speed stuff up :)

nathangrubb you mentioned that its possible to disable them, how would i go about this?

---

### Post by zPenguin on 2007-11-29
> **herbster said:**
> I get quite some lag in FF when opening tabs and switching while another is loading. Is this just FF or somethin' else? Especially pages like digg.com.

You could try Swiftfox, Its a Firefox compiled for your specific system, helped here to speed my firefox alot!

[http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm) Just try the install script, then it will install in /opt , you need to change the default browser too Swiftfox if you like it.

(the website has some problems loading for the moment)

---

### Post by cknight on 2007-11-29
One way to test the effect of few running processes is to try out a lightweight window manager in place of Gnome, such as Fluxbox, ICEWM, or Openbox.  I use Fluxbox and love it since it has much few running processes (currently at 95 with a bunch of programs open).  Once you install your lightweight window manager of choice, you can easily switch to it at login by choosing change session (or session type?  Sorry I don't use gdm much) from the options menu.  Then you can decide for yourself if you notice a speed difference. 

p.s. If you do decide to use Fluxbox, be sure to search the tutorial and tips forum for getting a right-click desktop menu setup.

---

### Post by -grubby on 2007-11-29
> **teryowen said:**
> I seem to have many things running also, not really slowing it down but i want to speed stuff up :)

nathangrubb you mentioned that its possible to disable them, how would i go about this?

well, at least in GNOME on Ubuntu you can go to system>administration>services and disable some

---

### Post by teryowen on 2007-11-29
> **nathangrubb said:**
> well, at least in GNOME on Ubuntu you can go to system>administration>services and disable some

Cool, thank you.

---

### Post by mysticrider92 on 2007-11-29
> **sethvath said:**
> If you dont experience any general slowness of the system it should be fine. 

Just for comparison, I have 192 processes running, 21% mem usage. System specs+background: 4gb ram, 2gb swap, FF with 14 tabs, xterm, ktorrent, amarok

Most days I run more programs than this and no problems with gutsy. On windows and mac osx, I'll start experiencing lags in system responsiveness

Hmmm, I have a full Gnome desktop with Firefox and a basic Compiz, and my htop only shows 53 total processes. 141 out of 1010mb ram and no swap usage.

You might want to trim down your startup services. Even if the computer does not seem slow now, you will see a speed improvement if you can stop some of those. And less processes means less chance of something messed up, but that is a very small concern for Linux.

---

### Post by herbster on 2007-11-29
I am using Openbox actually, and I just installed Swiftfox, it seems to be a tad bit faster. I also changed network.http.pipelining to "true" and network.dns.disableipv6 to "true," and it's a bit faster but not much. My firefox just seems sluggish, I can't figure out what is causing it. I'm curious if a complete reinstall would do the trick? Would I just apt-get remove and then download a .tar from firefox's site, or?

---

### Post by sethvath on 2007-11-30
> **mysticrider92 said:**
> Hmmm, I have a full Gnome desktop with Firefox and a basic Compiz, and my htop only shows 53 total processes. 141 out of 1010mb ram and no swap usage.

You might want to trim down your startup services. Even if the computer does not seem slow now, you will see a speed improvement if you can stop some of those. And less processes means less chance of something messed up, but that is a very small concern for Linux.
53 is definitely little. I could pare down the system processes to a minimum by disabling bluetooth, usb and printing (cups) but a marginal improvement of 100ms is of little consequence to me. On an older system I might do just that.

---

### Post by cknight on 2007-11-30
> **herbster said:**
> I am using Openbox actually...

Haha, I should have checked your process list first which would have told me the answer.  A more scientific approach would be to see how many processes are running on a clean boot.  Then startup each of your normal programs seeing how many processes are added from them.  This may then help pinpoint resource hogs?

When you use firefox, have you tried *just* firefox after boot?  E.g. elminate any possibility of contamination from other running processes.  After all, your normal workload consists of some heavy hitters.

---

### Post by herbster on 2007-11-30
Okay, I logged out and back in, and here's my autostart.sh from Openbox (progs that run on start-up):

```
# Programs to launch at startup
eval `cat $HOME/.fehbg` &
(sleep 2 && pypanel) &
(sleep 8 && conky) &
gnome-settings-daemon &
gnome-screensaver &
gnome-power-manager &
(sleep 2 && update-manager) &
##gnome-keyring-daemon &
##gnome-volume-manager &
(sleep 9 && amarok) &
(sleep 5 && blueman) &
#(sleep 9 && claws-mail) &
#(sleep 9 && amsn) &
restricted-manager --check &
```

It doesn't seem to be much. Basically it's blueman and amarok sitting in the tray at start-up and nothing else.

My total processes fresh on login are 185. I started FF and it jumps to about 193-195. It runs decently. I then launched a nautilus file browser, it only went to about 196 and FF wasn't much slower. I opened 5 more nautilus browsers and it wasn't much different in performance.

I think it might just be that I have FF running regularly with 2 windows and 1 window has at least 10 tabs all the time, the other about 6-7. I'm running a P4 3.4 EE with 1.2gb ram, 512mb 7600 GS card, I know it's more than decent enough to handle openbox and these programs. I can't think of any other reason for it slowing down a bit than a few windows and many tabs.

---

### Post by mysticrider92 on 2007-11-30
> **sethvath said:**
> 53 is definitely little. I could pare down the system processes to a minimum by disabling bluetooth, usb and printing (cups) but a marginal improvement of 100ms is of little consequence to me. On an older system I might do just that.

I don't think I really need the my process list shaved down so much, since my computer is fast enough, but I like the snappy feeling.

herbster: Have you tried the loopback mount trick? I can't remember the exact way to do it (I will dig it up later), but it can help a lot with apps like firefox.

---


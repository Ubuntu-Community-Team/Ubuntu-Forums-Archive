---
title: "firefox zombies at startup in system monior?  Is it a virus?"
date: 2008-05-07
forum: General Help
---

### Post by sefs on 2008-05-07
Hi all after booting when i look into system monitor

I see firefox zombies...what are they, why are they there...how to get rid of them?

This happens without me even starting firefox.

Pic attached.

---

### Post by kostkon on 2008-05-07
> **sefs said:**
> Hi all after booting when i look into system monitor

I see firefox zombies...what are they, why are they there...how to get rid of them?

This happens without me even starting firefox.

Pic attached.
I believe they are *Firefox* instances that didn't terminate and just stay there. Just kill them and they will not appear again.

If you want you can check the date that these instances were started by opening a terminal and giving
```
ps -fu *yourusername* | grep firefox
```

---

### Post by Zill on 2008-05-07
Just ignore them :-)

[URL="http://en.wikipedia.org/wiki/Zombie_process"]http://en.wikipedia.org/wiki/Zombie_process
[/URL]

---

### Post by damis648 on 2008-05-07
zombie simply put is nothing to be afraid of, its just a process that had not terminated. "Zombie" does not mean virus. (Linux can't REALLY get viruses :))

---

### Post by sefs on 2008-05-07
But they are there as soon as I boot up, everytime I boot up, and I'm not even using/started firefox.  Isn't that a strange occurance?

I mean i would understand if i had started firefox.

And they cannot be killed either...they are permanently there it seems.

---

### Post by jakupl on 2008-05-07
This will probably make them go away,

```
pkill firefox
```

---

### Post by sefs on 2008-05-08
Nope.  No cigar there either.

> **jakupl said:**
> This will probably make them go away,

```
pkill firefox
```

---

### Post by jakupl on 2008-05-08
can you post the output of:
```

ps -A
```

---

### Post by sefs on 2008-05-08
```

:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
   41 ?        00:00:00 kblockd/0
   44 ?        00:00:00 kacpid
   45 ?        00:00:00 kacpi_notify
  131 ?        00:00:00 kseriod
  169 ?        00:00:00 pdflush
  170 ?        00:00:00 pdflush
  171 ?        00:00:00 kswapd0
  210 ?        00:00:00 aio/0
 1468 ?        00:00:00 ksuspend_usbd
 1470 ?        00:00:00 khubd
 1487 ?        00:00:00 ata/0
 1490 ?        00:00:00 ata_aux
 1927 ?        00:00:00 scsi_eh_0
 1930 ?        00:00:00 scsi_eh_1
 2290 ?        00:00:00 scsi_eh_2
 2292 ?        00:00:00 scsi_eh_3
 2458 ?        00:00:00 kjournald
 2733 ?        00:00:00 udevd
 2904 ?        00:00:00 kgameportd
 3099 ?        00:00:00 kpsmoused
 6474 ?        00:00:00 kjournald
 6475 ?        00:00:00 kjournald
 6759 tty4     00:00:00 getty
 6760 tty5     00:00:00 getty
 6764 tty2     00:00:00 getty
 6765 tty3     00:00:00 getty
 6767 tty6     00:00:00 getty
 6925 ?        00:00:00 acpid
 6961 ?        00:00:00 kondemand/0
 7031 ?        00:00:00 syslogd
 7089 ?        00:00:00 dd
 7092 ?        00:00:00 klogd
 7114 ?        00:00:00 dbus-daemon
 7129 ?        00:00:00 system-tools-ba
 7163 ?        00:00:00 gdm
 7166 ?        00:00:00 gdm
 7171 tty7     00:01:45 Xorg
 7234 ?        00:00:00 avahi-daemon
 7235 ?        00:00:00 avahi-daemon
 7277 ?        00:00:00 cupsd
 7313 ?        00:00:00 mysqld_safe
 7355 ?        00:00:00 mysqld
 7357 ?        00:00:00 logger
 7372 ?        00:00:00 console-kit-dae
 7730 ?        00:00:04 clamd
 7826 ?        00:00:00 freshclam
 8102 ?        00:00:00 exim4
 8146 ?        00:00:00 gnump3d
 8151 ?        00:00:00 tuncfg
 8155 ?        00:00:00 hamachi
 8221 ?        00:00:03 privoxy
 8239 ?        00:00:00 nmbd
 8241 ?        00:00:00 smbd
 8253 ?        00:00:06 tor
 8293 ?        00:00:00 smbd
 8334 ?        00:00:00 xinetd
 8365 ?        00:00:00 dhcdbd
 8385 ?        00:00:00 hald
 8386 ?        00:00:00 hald-runner
 8419 ?        00:00:00 hald-addon-acpi
 8443 ?        00:00:00 hald-addon-inpu
 8453 ?        00:00:00 hald-addon-stor
 8473 ?        00:00:00 hald-addon-stor
 8493 ?        00:00:00 hcid
 8498 ?        00:00:00 btaddconn
 8499 ?        00:00:00 btdelconn
 8504 ?        00:00:00 bluetoothd-serv
 8508 ?        00:00:00 bluetoothd-serv
 8511 ?        00:00:00 krfcommd
 8551 ?        00:00:00 proftpd
 8586 ?        00:00:00 atd
 8605 ?        00:00:00 cron
 8701 ?        00:00:00 vmnet-bridge
 8719 ?        00:00:00 vmnet-netifup
 8728 ?        00:00:00 vmnet-dhcpd
 8738 ?        00:00:00 vmnet-netifup
 8750 ?        00:00:00 vmnet-dhcpd
 8755 ?        00:00:00 vmnet-natd
 8782 ?        00:00:00 apache2
 8835 ?        00:00:00 apache2
 8837 ?        00:00:00 apache2
 8838 ?        00:00:00 apache2
 8839 ?        00:00:00 apache2
 8840 ?        00:00:00 apache2
 8886 tty1     00:00:00 getty
 8893 ?        00:00:00 gconfd-2
 8895 ?        00:00:00 gnome-keyring-d
 8898 ?        00:00:00 gnome-session
 9002 ?        00:00:00 seahorse-agent
 9008 ?        00:00:00 dbus-daemon
 9009 ?        00:00:00 gnome-settings-
 9017 ?        00:00:00 pulseaudio
 9196 ?        00:00:00 gconf-helper
 9206 ?        00:00:04 gnome-screensav
 9210 ?        00:00:04 metacity
 9213 ?        00:00:09 gnome-panel
 9214 ?        00:00:01 nautilus
 9221 ?        00:00:00 bonobo-activati
 9224 ?        00:00:00 gvfsd
 9225 ?        00:00:00 bluetooth-apple
 9230 ?        00:00:01 update-notifier
 9234 ?        00:00:02 firestarter
 9238 ?        00:00:00 tracker-applet
 9239 ?        00:00:00 evolution-alarm
 9241 ?        00:00:16 trackerd
 9250 ?        00:00:00 python
 9252 ?        00:00:00 gnome-volume-ma
 9254 ?        00:00:00 gconfd-2
 9256 ?        00:00:00 gnome-power-man
 9261 ?        00:00:00 seahorse-agent
 9301 ?        00:00:00 evolution-data-
 9304 ?        00:00:00 gvfsd-burn
 9309 ?        00:00:01 deskbar-applet
 9312 ?        00:00:00 stickynotes_app
 9316 ?        00:00:00 evolution-excha
 9324 ?        00:00:00 trashapplet
 9327 ?        00:00:00 mixer_applet2
 9330 ?        00:00:02 gnome-netstatus
 9340 ?        00:00:00 gvfsd-trash
 9401 ?        00:00:00 gnome-vfs-daemo
 9417 ?        00:00:01 rt73Mlme
 9418 ?        00:00:00 rt73Cmd
 9439 ?        00:00:00 firefox <defunct>
 9457 ?        00:00:00 firefox <defunct>
 9479 ?        00:00:00 conky
 9949 ?        00:00:00 sshd
 9965 ?        00:00:00 firefox
 9977 ?        00:00:00 run-mozilla.sh
 9985 ?        00:03:55 firefox-bin
13203 ?        00:00:05 update-manager
21892 ?        00:00:00 gksu
21893 ?        00:00:14 synaptic
21899 ?        00:00:00 http
21974 ?        00:00:00 gnome-terminal
21976 ?        00:00:00 gnome-pty-helpe
21977 pts/0    00:00:00 bash
21988 pts/0    00:00:00 ps

```


from the list above the zombies are 

 9439 ?        00:00:00 firefox <defunct>
 9457 ?        00:00:00 firefox <defunct>

---

### Post by jakupl on 2008-05-08
What happens if you kill it all ?
```

pkill run-mozilla.sh
```

```
pkill firefox-bin
```

```
pkill firefox
```

```
pkill firefox*
```

---

### Post by sefs on 2008-05-10
Sadly, none of the above has any effect.

---

### Post by kostkon on 2008-05-10
> **sefs said:**
> Sadly, none of the above has any effect.
Do what *jakupl* recommends but add the *-9* option to *pkill* in order to force the termination of these processes, eg.:
```
pkill -9 firefox
```

---

### Post by sefs on 2008-05-13
That does not work either.

---

### Post by jakupl on 2008-05-13
that sure is funny.

try this. "It will uninstall firefox for a while."
```

sudo apt-get remove firefox-3.0
```

restart the computer.

```
ps -A
```

see if it still is there.

```
sudo apt-get install firefox-3.0
```

EDIT: This will not erase your bookmarks, plugins and stuff in firefox. "I tried it myself just to make sure".
      If you still are afraid, then backup your firefox dir. before doing anything else.

```
cp -r /home/user/.mozilla /home/user/.mozilla.bak
```

---

### Post by enoughsaid05 on 2008-12-26
Try the following

type in the command

user@userlaptop$ ps -axjf

Then it will print a list of trees of processes. Say if my bash process is a zombie process, it will show (just an example that i got from my command)

 6530 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 6561 ?        Sl     2:47 /usr/lib/firefox-3.0.5/firefox
 7351 ?        Sl     0:03 gnome-terminal
 7359 ?        S      0:00  \_ gnome-pty-helper
 7360 pts/0    Ss     0:00  \_ bash <defunct>
 8086 pts/0    R+     0:00      \_ ps -axf

So to remove that irritating defunct process, you kill the parent process by the command

user@userlaptop$ kill <PID of the parent process>

So in this case the parent process here is gnome-terminal because bash <defunct> comes under it, so I just have to kill my gnome terminal.

user@userlaptop$ kill 7351

hope this helps.

---

### Post by speed32219 on 2009-04-04
Thank you enoughsaid05, I learned something new, useful information you posted.

Can't wait to get off work to go home and try it on a project I've been working on with some issues.

---


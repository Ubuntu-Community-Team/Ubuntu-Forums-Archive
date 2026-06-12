---
title: "Completely disables periodic automatic apt updates."
date: 2022-10-22
forum: General Help
---

### Post by zhaohscas on 2022-10-22
Hi here,

I've the following settings in the files located under **/etc/apt/apt.conf.d**:

```

werner@X10DAi-00:/etc/apt/apt.conf.d$ ug -i ^apt:: 
20packagekit:APT::Update::Post-Invoke-Success {
10periodic:APT::Periodic::Update-Package-Lists "0";
10periodic:APT::Periodic::Download-Upgradeable-Packages "0";
10periodic:APT::Periodic::AutocleanInterval "0";
20auto-upgrades:APT::Periodic::Enable "0";
20auto-upgrades:APT::Periodic::Update-Package-Lists "0";
20auto-upgrades:APT::Periodic::Download-Upgradeable-Packages "0";
20auto-upgrades:APT::Periodic::Unattended-Upgrade "0";
20auto-upgrades:APT::Periodic::AutocleanInterval "0";
20auto-upgrades:APT::Periodic::Verbose "0";
20dbus:APT::Update::Post-Invoke-Success { "[ ! -f /var/run/dbus/system_bus_socket ] || /usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged || true"; };
00trustcdrom:APT::Authentication::TrustCDROM "true";
99synaptic:APT::Install-Recommends "true";
01autoremove-kernels:APT::NeverAutoRemove
20archive:APT::Archives::MaxAge "30";
20archive:APT::Archives::MinAge "2";
20archive:APT::Archives::MaxSize "500";
50appstream:APT::Update::Post-Invoke-Success {
50command-not-found:APT::Update::Post-Invoke-Success {
15update-stamp:APT::Update::Post-Invoke-Success {"touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";};

```

But I still noticed that the periodic automatic apt updates will happen at a certain time interval. I've puzzled by this problem. I would like to know how to completely disable periodic automatic apt updates of the packages corresponding to the repositories defined in **/etc/apt/sources.list** and **/etc/apt/sources.list.d**.

Regards,
Zhao

---

### Post by ajgreeny on 2022-10-22
Is this a server with no GUI or the default desktop version with gnome GUI, or another of the Ubuntu family?

If using the desktop with any DE/GUI you can go to **Software-Sources** from the menu system or use command terminal **software-properties-gtk**.

This will open a window and in the Updates tab you can turn off auto-updates for everything.
An alternative which I use is to uninstall the package ***unattended-upgrades***.

I prefer to choose when I update everything, usually once a day, but at a time of my choosing, not when the system decides.

---

### Post by zhaohscas on 2022-10-22
I'm using the desktop version and the package you mentioned has been removed by me some time before, as shown below:

```

werner@X10DAi-00:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal


werner@X10DAi-00:~$ dpkg -l unattended-upgrades | tail -1
rc  unattended-upgrades 2.3ubuntu0.1 all          automatic installation of security upgrades
```

In addition, I've also disabled the software update by selecting the "Never" option. But the problem reported here still happens.

Regards,
Zhao

---

### Post by &amp;KyT$0P# on 2022-10-22
Please post output from running the following command in Terminal -
```
systemctl status apt-daily apt-daily.timer apt-daily-upgrade apt-daily-upgrade.timer
```

---

### Post by zhaohscas on 2022-10-22
```
werner@X10DAi-00:~$ systemctl status apt-daily apt-daily.timer apt-daily-upgrade apt-daily-upgrade.timer
&#9679; apt-daily.service - Daily apt download activities
     Loaded: loaded (/lib/systemd/system/apt-daily.service; static; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:apt(8)

&#9679; apt-daily.timer - Daily apt download activities
     Loaded: loaded (/lib/systemd/system/apt-daily.timer; disabled; vendor preset: enabled)
     Active: inactive (dead)
    Trigger: n/a
   Triggers: &#9679; apt-daily.service

&#9679; apt-daily-upgrade.service - Daily apt upgrade and clean activities
     Loaded: loaded (/lib/systemd/system/apt-daily-upgrade.service; static; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:apt(8)

&#9679; apt-daily-upgrade.timer - Daily apt upgrade and clean activities
     Loaded: loaded (/lib/systemd/system/apt-daily-upgrade.timer; disabled; vendor preset: enabled)
     Active: inactive (dead)
    Trigger: n/a
   Triggers: &#9679; apt-daily-upgrade.service
```

---

### Post by &amp;KyT$0P# on 2022-10-22
Does masking those (and then rebooting) stop the automatic updates? -
```
sudo systemctl mask apt-daily{,-upgrade}{,.timer}
```

What about fully purging unattended-upgrades instead of just removing it?
```
sudo dpkg -P unattended-upgrades
```

If none of this helps, do the entries for these automatic updates in [FONT=Courier New]/var/log/apt/history.log[/FONT] contain [FONT=Courier New]Commandline:[/FONT] that gives any clue as to what's doing the automatic updates?

---

### Post by zhaohscas on 2022-10-23
I've tried all your above suggestions as follows:

```
werner@X10DAi-00:~$ sudo systemctl mask apt-daily{,-upgrade}{,.timer}
Created symlink /etc/systemd/system/apt-daily.service &#8594; /dev/null.
Created symlink /etc/systemd/system/apt-daily.timer &#8594; /dev/null.
Created symlink /etc/systemd/system/apt-daily-upgrade.service &#8594; /dev/null.
Created symlink /etc/systemd/system/apt-daily-upgrade.timer &#8594; /dev/null.

werner@X10DAi-00:~$ sudo dpkg -P unattended-upgrades
(Reading database ... 430888 files and directories currently installed.)
Purging configuration files for unattended-upgrades (2.3ubuntu0.1) ...
dpkg: warning: while removing unattended-upgrades, directory '/var/log/unattended-upgrades' not empty so not removed
Processing triggers for systemd (245.4-4ubuntu3.15) ...

```

As for whether they will solve this problem, we need to further observe the effect.

FYI, below is the content in the **/var/log/apt/history.log**:

```
werner@X10DAi-00:~$ cat /var/log/apt/history.log

Start-Date: 2022-10-04  20:42:26
Commandline: apt remove update-notifier
Requested-By: werner (1000)
Upgrade: update-manager-core:amd64 (1:20.04.10.9, 1:20.04.10.10), python3-distupgrade:amd64 (1:20.04.36, 1:20.04.39), python3-update-manager:amd64 (1:20.04.10.9, 1:20.04.10.10), ubuntu-release-upgrader-core:amd64 (1:20.04.36, 1:20.04.39)
Remove: update-manager:amd64 (1:20.04.10.9), ubuntu-release-upgrader-gtk:amd64 (1:20.04.36), update-notifier:amd64 (3.192.30.9)
End-Date: 2022-10-04  20:42:34

Start-Date: 2022-10-15  11:39:15
Commandline: apt install ntfs-3g
Requested-By: werner (1000)
Install: ntfs-3g:amd64 (1:2017.3.23AR.3-3ubuntu1.2)
Upgrade: libntfs-3g883:amd64 (1:2017.3.23AR.3-3ubuntu1.1, 1:2017.3.23AR.3-3ubuntu1.2)
End-Date: 2022-10-15  11:39:46

```

But the above commands were called by myself instead of the ones automatically run by apt update.

Regards,
Zhao

---

### Post by zhaohscas on 2022-10-29
The latest observation feedback: none of the above methods has solved the problems discussed here. I will still be disturbed by the automatic update of the system.

---

### Post by ian-weisser on 2022-10-29
> **zhaohscas said:**
> I will still be disturbed by the automatic update of the system.

I think we need to revisit assumptions. The output shows clearly that Unattended Upgrades has not run in weeks and cannot run anymore.

Exactly what is drawing your attention? What are you seeing or noticing? And how did you determine that it's "automatic-update" related?

---

### Post by zhaohscas on 2022-11-02
I've the following files in `/etc/apt/sources.list.d`:

```
[email]werner@X10DAi-00:/etc/apt/sources.list[/email].d$ ls
andreasbutti-ubuntu-xournalpp-master-focal.list       lyx-devel-ubuntu-release-focal.list.save  shutter-ubuntu-ppa-focal.list       yarn.list.save
andreasbutti-ubuntu-xournalpp-master-focal.list.save  microsoft-prod.list                       shutter-ubuntu-ppa-focal.list.save  zulip-desktop.list
google-chrome.list                                    microsoft-prod.list.save                  vscode.list                         zulip-desktop.list.save
google-chrome.list.save                               nodesource.list                           vscode.list.save
lyx-devel-ubuntu-release-focal.list                   nodesource.list.save                      yarn.list

```

The content of them is as follows:

```
werner@X10DAi-00:/etc/apt/sources.list[/email].d$ cat *
deb [http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu](http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu](http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu) focal main
deb [http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu](http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu](http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu) focal main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://ppa.launchpad.net/lyx-devel/release/ubuntu](http://ppa.launchpad.net/lyx-devel/release/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/lyx-devel/release/ubuntu](http://ppa.launchpad.net/lyx-devel/release/ubuntu) focal main
deb [http://ppa.launchpad.net/lyx-devel/release/ubuntu](http://ppa.launchpad.net/lyx-devel/release/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/lyx-devel/release/ubuntu](http://ppa.launchpad.net/lyx-devel/release/ubuntu) focal main
deb [arch=amd64] [https://packages.microsoft.com/ubuntu/20.04/prod](https://packages.microsoft.com/ubuntu/20.04/prod) focal main
deb [arch=amd64] [https://packages.microsoft.com/ubuntu/20.04/prod](https://packages.microsoft.com/ubuntu/20.04/prod) focal main
deb [signed-by=/usr/share/keyrings/nodesource.gpg] [https://deb.nodesource.com/node_16.x](https://deb.nodesource.com/node_16.x) focal main
deb-src [signed-by=/usr/share/keyrings/nodesource.gpg] [https://deb.nodesource.com/node_16.x](https://deb.nodesource.com/node_16.x) focal main
deb [signed-by=/usr/share/keyrings/nodesource.gpg] [https://deb.nodesource.com/node_16.x](https://deb.nodesource.com/node_16.x) focal main
deb-src [signed-by=/usr/share/keyrings/nodesource.gpg] [https://deb.nodesource.com/node_16.x](https://deb.nodesource.com/node_16.x) focal main
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) focal main
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) focal main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64,arm64,armhf] [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64,arm64,armhf] [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable main
deb [signed-by=/usr/share/keyrings/yarnkey.gpg] [https://dl.yarnpkg.com/debian](https://dl.yarnpkg.com/debian) stable main
deb [signed-by=/usr/share/keyrings/yarnkey.gpg] [https://dl.yarnpkg.com/debian](https://dl.yarnpkg.com/debian) stable main
deb [https://download.zulip.com/desktop/apt](https://download.zulip.com/desktop/apt) stable main
deb [https://download.zulip.com/desktop/apt](https://download.zulip.com/desktop/apt) stable main
```

The problem discussed here usually occurs when I boot up the system and try to log in to the desktop, and the automatic update of the repository associated with the above package sources are triggered periodically.

---

### Post by ian-weisser on 2022-11-02
> ...when I boot up the system and try to log in to the desktop, and the  automatic update of the repository associated with the above package  sources are triggered periodically

What output or screen feedback is telling you this? How did you determine that this is occurring?

---

### Post by zhaohscas on 2022-11-06
For additional information, I also noticed the following log when the problem occurred:


```
$ egrep -A1 -i  ' (get|hit|err|w):' /var/log/syslog*
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:1 http://dl.google.com/linux/chrome/deb stable InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Could not connect to 127.0.0.1:18888 (127.0.0.1). - connect (111: Connection refused)
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:2 https://dl.yarnpkg.com/debian stable InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Could not connect to 127.0.0.1:18888 (127.0.0.1). - connect (111: Connection refused)
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:3 https://deb.nodesource.com/node_16.x focal InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Could not connect to 127.0.0.1:18888 (127.0.0.1). - connect (111: Connection refused)
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:4 http://ppa.launchpad.net/andreasbutti/xournalpp-master/ubuntu focal InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Could not connect to 127.0.0.1:18888 (127.0.0.1). - connect (111: Connection refused)
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:5 https://packages.microsoft.com/ubuntu/20.04/prod focal InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Could not connect to 127.0.0.1:18888 (127.0.0.1). - connect (111: Connection refused)
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:6 http://packages.microsoft.com/repos/code stable InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Could not connect to 127.0.0.1:18888 (127.0.0.1). - connect (111: Connection refused)
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:7 https://download.zulip.com/desktop/apt stable InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Could not connect to 127.0.0.1:18888 (127.0.0.1). - connect (111: Connection refused)
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:8 http://ppa.launchpad.net/lyx-devel/release/ubuntu focal InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Unable to connect to 127.0.0.1:18888:
/var/log/syslog:Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Err:9 http://ppa.launchpad.net/shutter/ppa/ubuntu focal InRelease
/var/log/syslog-Nov  7 06:58:03 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]:   Unable to connect to 127.0.0.1:18888:
--
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Hit:10 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal InRelease
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:11 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates InRelease [114 kB]
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:12 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security InRelease [114 kB]
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:13 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/restricted Sources [45.1 kB]
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:14 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/multiverse Sources [21.5 kB]
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:15 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main Sources [528 kB]
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: message repeated 7 times: [ Get:15 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main Sources [528 kB]]
/var/log/syslog-Nov  7 06:58:04 X10DAi-00 avahi-daemon[1685]: Server startup complete. Host name is X10DAi-00-2.local. Local service cookie is 1064184198.
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:23 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/universe Sources [263 kB]
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:23 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/universe Sources [263 kB]
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:25 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main i386 Packages [745 kB]
/var/log/syslog:Nov  7 06:58:04 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: message repeated 2 times: [ Get:25 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main i386 Packages [745 kB]]
/var/log/syslog:Nov  7 06:58:05 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:28 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main amd64 Packages [2,214 kB]
/var/log/syslog:Nov  7 06:58:05 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: message repeated 3 times: [ Get:28 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main amd64 Packages [2,214 kB]]
/var/log/syslog:Nov  7 06:58:05 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:32 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main amd64 DEP-11 Metadata [274 kB]
/var/log/syslog:Nov  7 06:58:05 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:32 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main amd64 DEP-11 Metadata [274 kB]
/var/log/syslog:Nov  7 06:58:05 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:34 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates i386 Contents (deb) [65.2 MB]
/var/log/syslog:Nov  7 06:58:05 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:34 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates i386 Contents (deb) [65.2 MB]
/var/log/syslog-Nov  7 06:58:05 X10DAi-00 dbus-daemon[2961]: [session uid=1000 pid=2961] Activating via systemd: service name='org.freedesktop.Notifications' unit='dunst.service' requested by ':1.13' (uid=1000 pid=7726 comm="fcitx5 " label="unconfined")
--
/var/log/syslog:Nov  7 06:58:09 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:36 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates amd64 Contents (deb) [152 MB]
/var/log/syslog-Nov  7 06:58:09 X10DAi-00 appimagelauncherd[2952]: Directories to watch disappeared, unintegrating AppImages formerly found in there
--
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:37 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/main amd64 c-n-f Metadata [16.0 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:38 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/universe amd64 Packages [972 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:38 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/universe amd64 Packages [972 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:40 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/universe i386 Packages [697 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:41 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/universe amd64 DEP-11 Metadata [405 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:42 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/universe amd64 c-n-f Metadata [21.8 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:43 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:44 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/universe Sources [111 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:45 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/main Sources [252 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:46 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/main amd64 Packages [1,821 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:47 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/main i386 Packages [514 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:48 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/main amd64 DEP-11 Metadata [40.7 kB]
/var/log/syslog:Nov  7 06:58:19 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:49 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security i386 Contents (deb) [58.9 MB]
/var/log/syslog-Nov  7 06:58:19 X10DAi-00 systemd[2945]: espanso.service: Scheduled restart job, restart counter is at 13.
--
/var/log/syslog:Nov  7 06:58:22 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:50 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security amd64 Contents (deb) [139 MB]
/var/log/syslog-Nov  7 06:58:23 X10DAi-00 systemd[2945]: espanso.service: Scheduled restart job, restart counter is at 14.
--
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:51 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/main amd64 c-n-f Metadata [11.2 kB]
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:52 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/restricted amd64 Packages [1,289 kB]
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:53 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/restricted Translation-en [183 kB]
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:54 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/universe amd64 Packages [743 kB]
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:55 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/universe i386 Packages [566 kB]
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:56 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/universe Translation-en [137 kB]
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:57 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/universe amd64 DEP-11 Metadata [92.9 kB]
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:58 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/universe amd64 c-n-f Metadata [15.3 kB]
/var/log/syslog:Nov  7 06:58:31 X10DAi-00 /usr/lib/gdm3/gdm-x-session[7883]: Get:59 https://mirrors.tuna.tsinghua.edu.cn/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2,468 B]
/var/log/syslog-Nov  7 06:58:32 X10DAi-00 systemd[1]: systemd-hostnamed.service: Succeeded.

```

---

### Post by &amp;KyT$0P# on 2022-11-07
Since whatever is doing this is logging to syslog, maybe there would be something informative in the syslog lines that come immediately before the output from [FONT=Courier New]apt-get update[/FONT] ?

Might also be worth checking output of these two commands -
```
systemctl list-units
systemctl --global list-units
```

---

### Post by zhaohscas on 2022-12-05
Thank you halogen2,

Unfortunately, Ubuntu 20.04.3 LTS, the system where this problem occurred, crashed. As a result, I've installed the Ubuntu 22.10. So it's impossible for me to continue the discussion of this topic.

---


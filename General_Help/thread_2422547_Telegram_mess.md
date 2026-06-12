---
title: "Telegram mess"
date: 2019-07-09
forum: General Help
---

### Post by Scary Rob on 2019-07-09
I'll try to keep this brief. I'm using Kubuntu 18.04 and keep it constantly and fully updated.

I originally installed telegram from the "universe" repository. When I couldn't see a message from a friend (which turned out to be one of the new animated stickers), I removed it and libtgvoip because the semi-official Ubuntu repository version was waaaaay behind what was available via the PPA (atareao/telegram). I added the PPA and reinstalled telegram. Still couldn't see the sticker message, but at least I was on version 1.7.7 rather than 1.2.17 and had a chance of updating to 1.7.13 once the telegram devs got around to a linux version. Also, telegram had an "update" button below my contacts list. I clicked, and it closed and eventually reloaded. Everything was fine (but still v 1.7.7).

Today, the "update telegram" button reappeared. Half asleep, I clicked it (yes, I know I should have done it through apt for safety's sake). Telegram closed and didn't reload. Telegram was still listed in my software menus, but its icon had vanished from next to its name. I rebooted. Still no icon; Telegram refused to load.

I removed and reinstalled telegram via terminal. No change.

I removed telegram and deleted the ppa from my sources list. I then reinstalled telegram from the ubuntu "universe" repository. Still got a listing, no icon, and failure to load.

Any ideas? Apt log below.

history.log:
```
Start-Date: 2019-07-08  20:44:56
Remove: telegram-desktop:amd64 (1.2.17-1), libtgvoip1.0.3:amd64 (1.0.3-3)
End-Date: 2019-07-08  20:45:01

Start-Date: 2019-07-08  20:47:12
Commandline: apt install telegram
Requested-By: rob (1000)
Install: telegram:amd64 (1.7.7-0ubuntu2)
End-Date: 2019-07-08  20:47:16

Start-Date: 2019-07-09  15:39:21
Commandline: apt full-upgrade
Requested-By: rob (1000)
Upgrade: whoopsie:amd64 (0.2.62, 0.2.62ubuntu0.1), libwhoopsie0:amd64 (0.2.62, 0.2.62ubuntu0.1), apport:amd64 (2.20.9-0ubuntu7.6, 2.20.9-0ubuntu7.7), python3-apport:amd64 (2.20.9-0ubuntu7.6, 2.20.9-0ubuntu7.7), apport-kde:amd64 (2.20.9-0ubuntu7.6, 2.20.9-0ubuntu7.7), python3-problem-report:amd64 (2.20.9-0ubuntu7.6, 2.20.9-0ubuntu7.7)
End-Date: 2019-07-09  15:39:44

Start-Date: 2019-07-09  15:43:15
Commandline: apt remove telegram
Requested-By: rob (1000)
Remove: telegram:amd64 (1.7.7-0ubuntu2)
End-Date: 2019-07-09  15:43:21

Start-Date: 2019-07-09  15:43:58
Commandline: apt install telegram
Requested-By: rob (1000)
Install: telegram:amd64 (1.7.7-0ubuntu2)
End-Date: 2019-07-09  15:44:02

Start-Date: 2019-07-09  15:47:02
Commandline: apt remove telegram
Requested-By: rob (1000)
Remove: telegram:amd64 (1.7.7-0ubuntu2)
End-Date: 2019-07-09  15:47:03

Start-Date: 2019-07-09  15:49:49
Install: telegram-desktop:amd64 (1.2.17-1), libtgvoip1.0.3:amd64 (1.0.3-3, automatic)
End-Date: 2019-07-09  15:49:54

Start-Date: 2019-07-09  15:53:43
Commandline: apt autoremove
Requested-By: rob (1000)
Remove: python3-pyxattr:amd64 (0.6.0-2build2), libllvm7:amd64 (1:7-3~ubuntu0.18.04.1), libllvm7:i386 (1:7-3~ubuntu0.18.04.1), rtmpdump:amd64 (2.4+20151223.gitfa8646d.1-1), phantomjs:amd64 (2.1.1+dfsg-2)
End-Date: 2019-07-09  15:53:48

```

term.log:
```
Log started: 2019-07-08  20:44:56
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239058 files and directories currently installed.)
Removing telegram-desktop (1.2.17-1) ...
Removing libtgvoip1.0.3:amd64 (1.0.3-3) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Log ended: 2019-07-08  20:45:01

Log started: 2019-07-08  20:47:12
Selecting previously unselected package telegram.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239036 files and directories currently installed.)
Preparing to unpack .../telegram_1.7.7-0ubuntu2_amd64.deb ...
Unpacking telegram (1.7.7-0ubuntu2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Setting up telegram (1.7.7-0ubuntu2) ...
Telegram/
Telegram/Telegram
Telegram/Updater
Log ended: 2019-07-08  20:47:16

Log started: 2019-07-09  15:39:21
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239044 files and directories currently installed.)
Preparing to unpack .../0-whoopsie_0.2.62ubuntu0.1_amd64.deb ...
Unpacking whoopsie (0.2.62ubuntu0.1) over (0.2.62) ...
Preparing to unpack .../1-libwhoopsie0_0.2.62ubuntu0.1_amd64.deb ...
Unpacking libwhoopsie0:amd64 (0.2.62ubuntu0.1) over (0.2.62) ...
Preparing to unpack .../2-python3-problem-report_2.20.9-0ubuntu7.7_all.deb ...
Unpacking python3-problem-report (2.20.9-0ubuntu7.7) over (2.20.9-0ubuntu7.6) ...
Preparing to unpack .../3-python3-apport_2.20.9-0ubuntu7.7_all.deb ...
Unpacking python3-apport (2.20.9-0ubuntu7.7) over (2.20.9-0ubuntu7.6) ...
Preparing to unpack .../4-apport_2.20.9-0ubuntu7.7_all.deb ...
Unpacking apport (2.20.9-0ubuntu7.7) over (2.20.9-0ubuntu7.6) ...
Preparing to unpack .../5-apport-kde_2.20.9-0ubuntu7.7_all.deb ...
Unpacking apport-kde (2.20.9-0ubuntu7.7) over (2.20.9-0ubuntu7.6) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-21) ...
ureadahead will be reprofiled on next reboot
Setting up python3-problem-report (2.20.9-0ubuntu7.7) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for systemd (237-3ubuntu10.24) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Setting up libwhoopsie0:amd64 (0.2.62ubuntu0.1) ...
Setting up python3-apport (2.20.9-0ubuntu7.7) ...
Setting up whoopsie (0.2.62ubuntu0.1) ...
Setting up apport (2.20.9-0ubuntu7.7) ...
apport-autoreport.service is a disabled or a static unit, not starting it.
Setting up apport-kde (2.20.9-0ubuntu7.7) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Log ended: 2019-07-09  15:39:44

Log started: 2019-07-09  15:43:15
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239043 files and directories currently installed.)
Removing telegram (1.7.7-0ubuntu2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Log ended: 2019-07-09  15:43:21

Log started: 2019-07-09  15:43:58
Selecting previously unselected package telegram.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239037 files and directories currently installed.)
Preparing to unpack .../telegram_1.7.7-0ubuntu2_amd64.deb ...
Unpacking telegram (1.7.7-0ubuntu2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Setting up telegram (1.7.7-0ubuntu2) ...
Telegram/
Telegram/Telegram
Telegram/Updater
Log ended: 2019-07-09  15:44:02

Log started: 2019-07-09  15:47:02
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239043 files and directories currently installed.)
Removing telegram (1.7.7-0ubuntu2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Log ended: 2019-07-09  15:47:03

Log started: 2019-07-09  15:49:49
Selecting previously unselected package libtgvoip1.0.3:amd64.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239037 files and directories currently installed.)
Preparing to unpack .../libtgvoip1.0.3_1.0.3-3_amd64.deb ...
Unpacking libtgvoip1.0.3:amd64 (1.0.3-3) ...
Selecting previously unselected package telegram-desktop.
Preparing to unpack .../telegram-desktop_1.2.17-1_amd64.deb ...
Unpacking telegram-desktop (1.2.17-1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Setting up libtgvoip1.0.3:amd64 (1.0.3-3) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Setting up telegram-desktop (1.2.17-1) ...
Log ended: 2019-07-09  15:49:54

Log started: 2019-07-09  15:53:43
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239059 files and directories currently installed.)
Removing libllvm7:amd64 (1:7-3~ubuntu0.18.04.1) ...
Removing libllvm7:i386 (1:7-3~ubuntu0.18.04.1) ...
Removing phantomjs (2.1.1+dfsg-2) ...
Removing python3-pyxattr (0.6.0-2build2) ...
Removing rtmpdump (2.4+20151223.gitfa8646d.1-1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Log ended: 2019-07-09  15:53:48
```

---

### Post by #&amp;thj^% on 2019-07-09
I prefer to use this method for my installs:
```
wget -O- https://telegram.org/dl/desktop/linux | sudo tar xJ -C /opt/
```
and:
```
sudo ln -s /opt/Telegram/Telegram /usr/local/bin/telegram-desktop

```
Current version "1.7.14"
To call it use:
```
telegram-desktop

```

---

### Post by Scary Rob on 2019-07-09
Cheers! I'll give it a go tomorrow. I might do a purge of the config files first just to make sure there's nothing in them causing the problem

---

### Post by Scary Rob on 2019-07-10
Thanks, 1fallen. As a workaround, it's working well.

---

### Post by #&amp;thj^% on 2019-07-10
Great news! But to add it's not really a work-around but more of a just different method to install when our version's are very outdated.

---


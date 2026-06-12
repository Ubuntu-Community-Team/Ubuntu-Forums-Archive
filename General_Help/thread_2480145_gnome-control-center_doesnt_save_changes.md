---
title: "gnome-control-center doesnt save changes"
date: 2022-10-20
forum: General Help
---

### Post by linuxuserdimitry on 2022-10-20
Dear readers and linux experts,this is my first thread, creating after searching for much hours without success. Also i want to apologize for incorrect sentences.My settings in gnome-control-center just wont stay after reboot/log out (same for favourite apps on dash to panel), probably cause of false permissions. Sadly couldnt find informations about correct permissions and ownerships on the .config .cache .local etc. problem related files (and symlinks..?). I guess thats the point where i should share the the permissions and ownerships on those inside /home/$USER : ```
$ ls -al | grep ".*"
total 975584
drwxr-xr-x 71 godshot godshot      4096 Okt 20 19:11 .
drwxr-xr-x  6 root    root        4096 Sep 18  2020 ..
drwxr-xr-x  2 godshot godshot      4096 Mai 20 02:34 .android
-rw-rw----  1 godshot godshot        24 Jun 21 04:07 .aspell.en.prepl
-rw-rw----  1 godshot godshot        31 Jun 21 04:07 .aspell.en.pws
-rw-rw----  1 godshot godshot      169 Jun 15 05:37 banner.filed
-rw-rw----  1 godshot godshot      1042 Feb  4  2022 .bash_history
-rw-rw----  1 godshot godshot      220 Dez 29  2021 .bash_logout
-rw-rw----  1 godshot godshot      3866 Okt 17 15:15 .bashrcd
rwxr-xr-x  3 godshot godshot      4096 Okt 17 16:45 .bundled
rwxrwxr-x 41 godshot godshot    4096 Okt 20 11:19 .cache
-rw-rw----  1 godshot godshot        1 Okt 20 03:17 commands.txt
drwxrwxr-x 53 godshot godshot      4096 Okt 20 10:54 .config
drwxr-xr-x 11 godshot godshot      4096 Jan 24  2022 conky-manager
-rw-rw----  1 godshot godshot      4245 Jul 14  2014 .conkyrc
drwxr-xr-x  4 godshot godshot      4096 Jan  4  2022 create_apd
rwxr-xr-x  8 godshot godshot      4096 Jan 26  2022 .cxoffice
drwxr-xr-x  3 godshot godshot      4096 Jan  1  2022 .degit
-rw-rw----  1 godshot godshot        24 Feb  6  2022 .dmrc
drwx------  2 godshot godshot      4096 Okt 20 16:13 .gconf
drwxr-xr-x  3 godshot godshot      4096 Okt 17 17:48 .gemd
rwxr-xr-x  3 godshot godshot      4096 Mai 20 02:15 .gnome
drwxr-xr-x  6 godshot godshot      4096 Okt 20 14:20 gnome-browser-connector
drwxr-xr-x  4 godshot godshot      4096 Okt 20 17:44 .gnupg
drwxr-xr-x  3 godshot godshot      4096 Okt 17 17:24 go
-rw-rw----  1 godshot godshot      245 Jan 26  2022 .gtkrc-2.0
drwxrwxr-x  6 godshot godshot      4096 Jan 23  2022 .local
drwxr-xr-x 12 godshot godshot      4096 Apr 30 12:12 .oh-my-zsh
-rw-rw----  1 godshot godshot        72 Dez 29  2021 .selected_editor
-rw-rw----  1 godshot godshot        10 Dez 29  2021 .shell.pre-oh-my-zsh
drwx------  8 godshot godshot      4096 Okt 20 13:47 snapd
rwxr-xr-x  4 godshot godshot      4096 Sep 23 10:34 .sqlmap
drwxr-xr-x  2 godshot godshot    4096 Jan  1  2022 .ssh
-rw-rw----  1 godshot godshot        0 Dez 29  2021 .sudo_as_admin_successful
drwxr-xr-x  2 godshot godshot      4096 Feb 27  2022 .swt
drwxr-xr-x  2 godshot godshot      4096 Dez 29  2021 .synaptic
drwxr-xr-x  8 godshot godshot      4096 Jan 21  2022 .ubunsys
-rw-rw----  1 godshot godshot        49 Okt 17 15:17 .Xauthority
-rw-rw----  1 godshot godshot    49647 Okt 19 20:58 .zcompdump
-rw-rw----  1 godshot godshot    51089 Okt 19 18:23 .zcompdump-AK47-5.8
-rw-rw----  1 godshot godshot    51140 Okt 20 10:27 .zcompdump-AK47-5.8.1
-rw-rw----  1 godshot godshot    52446 Okt 18 02:33 .zcompdump-AK47-5.9
-rw-rw----  1 godshot godshot    51256 Jan 21  2022 .zcompdump-ubuntugamepack-5.8
-rw-rw----  1 godshot godshot    212022 Okt 20 19:11 .zsh_history
-rw-rw----  1 godshot godshot    31297 Jan  2  2022 .zsh_history_bad
-rw-rw----  1 godshot godshot      5926 Okt 19 21:26 .zshrc
-rw-rw----  1 godshot godshot      5900 Okt 18 18:50 .zshrcbackup
```

cause i did 
```
sudo -i -u $USER 
``` and it changed something from HOME=/root an output of sudo env:
```
$ sudo env

MAIL=/var/mail/root
LOGNAME=root
USER=root
HOME=/root
SHELL=/usr/bin/zsh
SUDO_COMMAND=/usr/bin/env
SUDO_USER=godshot
SUDO_UID=1000SUDO_GID=1000
```
some of the commands i tried while fixing where:

```

sudo chmod -R a+rwX,o-rw /home/$USER 
chmod a+rwx /home/$USER
sudo find /home/godshot/* -type d -print0 | xargs -0 chmod 0775
sudo find /home/godshot/* -type d -print0 | xargs -0 chmod "0770"
sudo find /home/godshot -type d -print0 | sudo xargs -0 chown -R godshot
```

some chown commands on home files where with -hR. If anything relevant is missing ill append it, just say what. Tried a lot of commands probably just working on the wrong side to fix my issue.T hanks in advice for anything that could help.

---


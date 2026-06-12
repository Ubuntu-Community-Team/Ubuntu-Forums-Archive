---
title: "CHIRP accessing serial ports"
date: 2023-05-28
forum: General Help
---

### Post by savvikas on 2023-05-28
First of all this is not the first time someone has an issue with setting up chirp ([https://ubuntuforums.org/showthread.php?t=2356856](https://ubuntuforums.org/showthread.php?t=2356856)) but as a new user am trying to overcome it. The major difference is that my device recognizes my programming cable. At the moment I managed ([https://ubuntuforums.org/showthread.php?t=2487185](https://ubuntuforums.org/showthread.php?t=2487185)) with the help of user : [**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("https://ubuntuforums.org/member.php?u=1961578") to install the CHIRP software using pipx as per instructions posted on the official site of CHIRP ([https://chirp.danplanet.com/projects/chirp/wiki/ChirpOnLinux](https://chirp.danplanet.com/projects/chirp/wiki/ChirpOnLinux)). But now I cannot add me as a user who wants to use CHIRP to the group that owns the serial ports.

According to the instructions I need to [I][U][B]" First determine the USB port of your device, and then the following command should add your user to the proper group:
Note that "ttyUSB0" should be replaced with the actual device that  identifies your connection to the radio and that "$USER" is a system  variable that identifies the username of the individual running the  command."[/B][/U][/I]

so firstly I identified the usb port name using the command $lsusb:
```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 005: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 007 Device 007: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port / Mobile Action MA-8910P
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
afterwards I already know the name of my user which is **savvikas** so i type and execute the command below:
```
sudo usermod -a -G $(stat -c %G /dev/0bda:0158) $savvikas
```

After running the command above I receive the below error:
```
stat: cannot statx '/dev/0bda:0158': No such file or directory
usermod: option requires an argument -- 'G'
Usage: usermod [options] LOGIN

Options:
  -a, --append                  append the user to the supplemental GROUPS
                                mentioned by the -G option without removing
                                the user from other groups
  -b, --badname                 allow bad names
  -c, --comment COMMENT         new value of the GECOS field
  -d, --home HOME_DIR           new home directory for the user account
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP as new primary group
  -G, --groups GROUPS           new list of supplementary GROUPS
  -h, --help                    display this help message and exit
  -l, --login NEW_LOGIN         new value of the login name
  -L, --lock                    lock the user account
  -m, --move-home               move contents of the home directory to the
                                new location (use only with -d)
  -o, --non-unique              allow using duplicate (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new password
  -P, --prefix PREFIX_DIR       prefix directory where are located the /etc/* files
  -r, --remove                  remove the user from only the supplemental GROUPS
                                mentioned by the -G option without removing
                                the user from other groups
  -R, --root CHROOT_DIR         directory to chroot into
  -s, --shell SHELL             new login shell for the user account
  -u, --uid UID                 new UID for the user account
  -U, --unlock                  unlock the user account
  -v, --add-subuids FIRST-LAST  add range of subordinate uids
  -V, --del-subuids FIRST-LAST  remove range of subordinate uids
  -w, --add-subgids FIRST-LAST  add range of subordinate gids
  -W, --del-subgids FIRST-LAST  remove range of subordinate gids
  -Z, --selinux-user SEUSER     new SELinux user mapping for the user account


```

I believe that the instructions are correct but due to my inexperience I am doing something wrong.
I would be very happy if someone could help me

Kind regards, 

Savvikas

---

### Post by jeremy31 on 2023-05-28
Try ```
sudo gpasswd --add ${USER} dialout
```
Then you might have to log out or reboot, then try CHIRP again.  Your USB device for CHIRP isn't 0bda:0158 as that is some sdcard reader, your device is shown as ```
Bus 007 Device 007: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port / Mobile Action MA-8910P
```

---

### Post by savvikas on 2023-05-28
It finally worked thank you very much can you explain what the command you gave me means? Have you by using superuser made my user admin of the group?
[IMG]https://ibb.co/RhRZP0T[/IMG]

---

### Post by jeremy31 on 2023-05-28
Your user is now part of the group needed to use ttyusb0.  I only knew about it because of issues I had with amateur radio software I tried using in the past

---


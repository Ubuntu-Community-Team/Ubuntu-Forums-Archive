---
title: "ubuntu server always shutdown"
date: 2023-05-30
forum: General Help
---

### Post by logging on 2023-05-30
[FONT=arial][COLOR=#202124]ubuntu has a server. They asked for support. The server did not have a problem when I connected earlier. Later they said that he was constantly shutting himself down. I said did you make any changes? They uploaded a gui. Could the constant shutdown be caused by this?[/COLOR][/FONT]

Ubuntu 22.04.2 LTS

I do disk and ram  test - passed


> root@server1:~# sudo journalctl -b -1 -e
May 30 15:19:17 server1 gnome-shell[2751]: Can't update stage views actor <unnamed>[<MetaWindowGroup>:0x55fef65d4350] is on because it needs an allocation.
May 30 15:19:17 server1 gnome-shell[2751]: Can't update stage views actor <unnamed>[<MetaWindowActorX11>:0x55fef7802750] is on because it needs an allocation.
May 30 15:19:17 server1 gnome-shell[2751]: Can't update stage views actor <unnamed>[<MetaSurfaceActorX11>:0x55fef78066e0] is on because it needs an allocation.
May 30 15:23:49 server1 sshd[3530]: fatal: Timeout before authentication for 192.168.50.68 port 60321
May 30 15:27:27 server1 sshd[3543]: Accepted password for szapick from 10.212.134.4 port 63452 ssh2
May 30 15:27:27 server1 sshd[3543]: pam_unix(sshd:session): session opened for user szapick(uid=1000) by (uid=0)
May 30 15:27:27 server1 systemd-logind[1521]: New session 6 of user tara.
May 30 15:27:27 server1 systemd[1]: Started Session 6 of User szapick.
May 30 15:27:28 server1 gnome-software[2895]: Failed to reload changed app filter: App filtering is globally disabled
May 30 15:27:28 server1 gnome-software[2895]: Failed to reload changed app filter: App filtering is globally disabled
May 30 15:27:42 server1 sudo[3613]: szapick : TTY=pts/2 ; PWD=/home/szapick ; USER=root ; COMMAND=/usr/bin/su -
May 30 15:27:42 server1 sudo[3613]: pam_unix(sudo:session): session opened for user root(uid=0) by szapick(uid=1000)
May 30 15:27:42 server1 su[3615]: (to root) root on pts/3
May 30 15:27:42 server1 su[3615]: pam_unix(su-l:session): session opened for user root(uid=0) by szapick(uid=0)
May 30 15:28:19 server1 systemd[1]: Starting GRUB failed boot detection...
May 30 15:28:19 server1 systemd[1]: grub-initrd-fallback.service: Deactivated successfully.
May 30 15:28:19 server1 systemd[1]: Finished GRUB failed boot detection.
May 30 15:28:36 server1 systemd[1]: Starting GRUB failed boot detection...
May 30 15:28:36 server1 systemd[1]: grub-initrd-fallback.service: Deactivated successfully.
May 30 15:28:36 server1 systemd[1]: Finished GRUB failed boot detection.
May 30 15:28:58 server1 systemd[1]: Starting Cleanup of Temporary Directories...
May 30 15:28:58 server1 systemd[1]: systemd-tmpfiles-clean.service: Deactivated successfully.
May 30 15:28:58 server1 systemd[1]: Finished Cleanup of Temporary Directories.
May 30 15:33:12 server1 sshd[3654]: Accepted password for szapick from 192.168.50.68 port 60403 ssh2
May 30 15:33:12 server1 sshd[3654]: pam_unix(sshd:session): session opened for user szapick(uid=1000) by (uid=0)
May 30 15:33:12 server1 systemd-logind[1521]: New session 7 of user szapick.
May 30 15:33:12 server1 systemd[1]: Started Session 7 of User tara.
May 30 15:33:13 server1 gnome-software[2895]: Failed to reload changed app filter: App filtering is globally disabled
May 30 15:33:13 server1 gnome-software[2895]: Failed to reload changed app filter: App filtering is globally disabled
May 30 15:39:27 server1 ModemManager[1535]: <info> [sleep-monitor-systemd] system is about to suspend
May 30 15:39:27 server1 NetworkManager[1500]: <info> [1685450367.1776] manager: sleep: sleep requested (sleeping: no enabled: yes)
May 30 15:39:27 server1 NetworkManager[1500]: <info> [1685450367.1778] manager: NetworkManager state is now ASLEEP
May 30 15:39:27 server1 systemd[1]: Reached target Sleep.
May 30 15:39:27 server1 systemd[1]: Starting Record successful boot for GRUB...
May 30 15:39:27 server1 systemd[1]: Starting System Suspend...
May 30 15:39:27 server1 systemd-sleep[3759]: Entering sleep state 'suspend'...
May 30 15:39:27 server1 systemd[1]: grub-common.service: Deactivated successfully.





> root@szadata:~# dmesg -T | grep -i "panic\|error\|hang"[Tue May 30 15:57:29 2023]   zhaoxin   Shanghai
[Tue May 30 15:57:31 2023] ERST: Error Record Serialization Table (ERST) support is initialized.
[Tue May 30 15:57:32 2023] i8042: probe of i8042 failed with error -5
[Tue May 30 15:57:32 2023] RAS: Correctable Errors collector initialized.
[Tue May 30 15:57:36 2023] loop0: detected capacity change from 0 to 8
[Tue May 30 15:57:36 2023] loop1: detected capacity change from 0 to 129600
[Tue May 30 15:57:36 2023] loop2: detected capacity change from 0 to 129952
[Tue May 30 15:57:36 2023] loop3: detected capacity change from 0 to 497424
[Tue May 30 15:57:36 2023] loop4: detected capacity change from 0 to 716168
[Tue May 30 15:57:36 2023] loop5: detected capacity change from 0 to 187776
[Tue May 30 15:57:36 2023] loop6: detected capacity change from 0 to 229272
[Tue May 30 15:57:36 2023] loop7: detected capacity change from 0 to 102072
[Tue May 30 15:57:36 2023] loop8: detected capacity change from 0 to 109032
[Tue May 30 15:59:38 2023] CIFS: No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3.1.1), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3.1.1 (or even SMB3 or SMB2.1) specify vers=1.0 on mount.
[Tue May 30 15:59:40 2023] loop9: detected capacity change from 0 to 8

---

### Post by TheFu on 2023-05-30
Yes.  GUI tools often setup sleep/hibernation modes.

---

### Post by logging on 2023-05-30
Thank you 

[FONT=arial][COLOR=#202124]I disabled the gui interface. How else can I fix[/COLOR][/FONT]

---

### Post by TheFu on 2023-05-30
> **logging said:**
> Thank you 
I disabled the gui interface. How else can I fix

Perhaps try disabling the sleep and/or hibernation?
Be certain to charge the client time and materials for any work you do after walking away.  $300/hr will get their attention, especially if all you do it put the system back to what it was.  BTW, you might want to use OS-level snapshots to make putting back stuff easy ... though if you have the system setup for automatic security patches, that wouldn't be good.  LVM or ZFS can be used for this.  I wouldn't trust BTRFS in production, but I suspect lots of other people do. Obviously, retaining snapshots will eventually eat all the storage, so some kind of snapshot rotation/management will

Please use normal fonts and colors when posting here.

---

### Post by MAFoElffen on 2023-05-30
First check for the presence of the dconf/gstettings database... dconf is installed during a desktop installation of most gnome based desktops. It contains the power management settings, along with a lot of other settings in a Desktop Environment.

To see if it is still installed:
```

apt list dconf* --installed

```
Then check these:
```

mafoelffen@Mikes-ThinkPad-T520:~$ echo $XDG_DATA_DIRS
/usr/share/gnome-xorg:/usr/share/gnome:/usr/local/share:/usr/share:/var/lib/snapd/desktop
mafoelffen@Mikes-ThinkPad-T520:~$ set | grep XDG
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome-xorg:/etc/xdg
XDG_CURRENT_DESKTOP=GNOME
XDG_DATA_DIRS=/usr/share/gnome-xorg:/usr/share/gnome:/usr/local/share:/usr/share:/var/lib/snapd/desktop
XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/mafoelffen
XDG_MENU_PREFIX=gnome-
XDG_RUNTIME_DIR=/run/user/1000
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
XDG_SESSION_CLASS=user
XDG_SESSION_DESKTOP=gnome-xorg
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
XDG_SESSION_TYPE=x11
    local -a dirs=(${BASH_COMPLETION_USER_DIR:-${XDG_DATA_HOME:-$HOME/.local/share}/bash-completion}/completions);
    for dir in ${XDG_DATA_DIRS:-/usr/local/share:/usr/share};
mafoelffen@Mikes-ThinkPad-T520:~$ echo $XDG_RUNTIME_DIR
/run/user/1000

```
The RedHat Doc's say it's in this directory (and in Ubuntu there are items there):
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls /etc/dconf/db/
ibus  ibus.d

```
For each user, they are here: ~/.config/dconf/user
```

mafoelffen@Mikes-ThinkPad-T520:~$ file ~/.config/dconf/user
/home/mafoelffen/.config/dconf/user: GVariant Database file, version 0

```
If it is present, then do
```

gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type "nothing"

```
That would be the easy thing to do... To tell it not to do anything when it is idle.

dconf didn't use to pull in many dependencies when it got installed as a package when it was started by init. But that was when it was only one package, and before it got converted into a systemd service. I haven't tried to remove dconf since it was added as a 'service'... So I that may be new ground for me.

---

### Post by TheFu on 2023-05-30
A 20.04 server, installed in the last 2 weeks:
```
$ sudo apt-get remove dconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Package 'dconf' is not installed, so not removed
[/B]0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```
Purge that package on servers.

```
$ ls -al  /etc/dconf/db/
total 8
drwxr-xr-x 2 root root 4096 Mar 11  2020 ./
drwxr-xr-x 3 root root 4096 Mar 14 18:42 ../
```
Nothing in there.

Charge time and materials to fix customer-caused breakage.

---

### Post by MAFoElffen on 2023-05-30
But on current Buntu desktops, since SystemD, they changed the package names:
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list dconf* --installed
Listing... Done
dconf-cli/jammy,now 0.40.0-3 amd64 [installed,automatic]
dconf-editor/jammy,now 3.38.3-3 amd64 [installed]
dconf-gsettings-backend/jammy,now 0.40.0-3 amd64 [installed,automatic]
dconf-service/jammy,now 0.40.0-3 amd64 [installed,automatic]

```
So would try something like
```

for i in dconf-cli dconf-editor dconf-settings-backend dconf-service; do sudo apt remove --purge $i; done

```
Or just simply
```

sudo apt remove --purge dconf*

```
The remove otpion will uninstall dconf apps. --purge will remove the instances of the dconf database files with it.

---

### Post by MAFoElffen on 2023-05-31
LOL. I was answering someone else about a power profile question and remember another thing to check and change
```

# which powerproiflesctl
/usr/bin/powerprofilesctl

# powerprofilesctl list
  performance:
    Driver:     intel_pstate
    Degraded:   no

* balanced:
    Driver:     intel_pstate

  power-saver:
    Driver:     intel_pstate

# powerprofiles set performance

# powerprofilesctl list
* performance:
    Driver:     intel_pstate
    Degraded:   no

  balanced:
    Driver:     intel_pstate

  power-saver:
    Driver:     intel_pstate

```
This is what I needed to do to that machine, which has a GUI-on-demand, but cannot go to sleep. Because of the ZFS raidz pools, if it goes to sleep (the disks), then the disks drop offline, then the pools go to an unavailable status. Not good.

---

### Post by TheFu on 2023-05-31
Again, on an Ubuntu Server 20.04 install:

```
$ sudo powerprofilesctl list
sudo: powerprofilesctl: command not found

$ locate powerprofilesctl

$
```
BTW, I added a WM to this system, but no DE.  If you want to be more customer focused, doing something similar might bridge the difference between full DE and no GUI at all?  I did have to manually setup xinit/startx, slim, and my WM of choice, fvwm.  This leaves the server alone and doesn't radically change the config.  I see ZERO popups and power management is of the type controlled by the server alone.

---


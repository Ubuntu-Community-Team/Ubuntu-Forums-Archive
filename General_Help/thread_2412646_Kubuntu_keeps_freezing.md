---
title: "Kubuntu keeps freezing"
date: 2019-02-15
forum: General Help
---

### Post by speedymcs on 2019-02-15
Hi, recently, apparently one of the hard drives of my work machine failed (I had asked about that in this thread: [https://ubuntuforums.org/showthread.php?t=2412024](https://ubuntuforums.org/showthread.php?t=2412024)).
I now received back the machine from our IT, with a fresh Kubuntu 18.04.2 installed. Previously, I was using Xubuntu 16.04. So far Kubuntu is running very unstable. At seemingly random actions, sometimes opening a new tab in either Firefox or Chromium, sometimes upon starting VS Code, the whole GUI freezes, except for the cursor. I can freely move it around but everything else is completely frozen in time. I let it stay like that for half an hour once and nothing happened at all, the mouse reacts and the cursor looks normal, but the keyboard does nothing, only a hard reset helps. 
After the last time I tried to search the logs for warnings and errors using this handy command recommended by a user in the above linked thread:
```
[COLOR=#000000][FONT=&amp]$ egrep -i 'error|warn' /var/log/*g[/FONT][/COLOR]
```

Here is the most recent log output:

```

/var/log/kern.log:Feb 14 14:16:22 PCNAME kernel: [    0.913051] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 14 14:16:22 PCNAME kernel: [    1.129578] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 14 14:16:22 PCNAME kernel: [    2.684213] sas: ata7: end_device-1:0: dev error handler
/var/log/kern.log:Feb 14 14:16:22 PCNAME kernel: [    3.141142] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 14 14:32:04 PCNAME kernel: [    0.909124] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 14 14:32:04 PCNAME kernel: [    1.121733] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 14 14:32:04 PCNAME kernel: [    2.652173] sas: ata7: end_device-1:0: dev error handler
/var/log/kern.log:Feb 14 14:32:04 PCNAME kernel: [    3.110959] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 14 14:41:32 PCNAME kernel: [    0.909055] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 14 14:41:32 PCNAME kernel: [    1.125692] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 14 14:41:32 PCNAME kernel: [    2.684195] sas: ata7: end_device-3:0: dev error handler
/var/log/kern.log:Feb 14 14:41:32 PCNAME kernel: [    3.128693] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 14 14:52:36 PCNAME kernel: [    0.920935] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 14 14:52:36 PCNAME kernel: [    1.133885] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 14 14:52:36 PCNAME kernel: [    2.972241] sas: ata7: end_device-3:0: dev error handler
/var/log/kern.log:Feb 14 14:52:36 PCNAME kernel: [    3.430882] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 14 14:52:55 PCNAME kernel: [   23.836086] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 14 15:18:27 PCNAME kernel: [    0.921274] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 14 15:18:27 PCNAME kernel: [    1.133792] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 14 15:18:27 PCNAME kernel: [    2.972273] sas: ata7: end_device-1:0: dev error handler
/var/log/kern.log:Feb 14 15:18:27 PCNAME kernel: [    3.431813] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 14 15:18:41 PCNAME kernel: [   18.132253] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 14 16:35:51 PCNAME kernel: [ 4648.355054] nouveau 0000:04:00.0: fifo: SCHED_ERROR 0a [CTXSW_TIMEOUT]
/var/log/kern.log:Feb 14 16:38:31 PCNAME kernel: [    0.920311] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 14 16:38:31 PCNAME kernel: [    1.137652] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 14 16:38:31 PCNAME kernel: [    2.972226] sas: ata7: end_device-6:0: dev error handler
/var/log/kern.log:Feb 14 16:38:31 PCNAME kernel: [    5.429736] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 14 16:38:31 PCNAME kernel: [    5.691233] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 14 16:40:48 PCNAME kernel: [    0.920957] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 14 16:40:48 PCNAME kernel: [    1.133670] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 14 16:40:48 PCNAME kernel: [    2.972246] sas: ata7: end_device-0:0: dev error handler
/var/log/kern.log:Feb 14 16:40:48 PCNAME kernel: [    3.636586] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 14 16:41:10 PCNAME kernel: [   26.711446] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 14 16:54:12 PCNAME kernel: [    0.921257] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 14 16:54:12 PCNAME kernel: [    1.133711] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 14 16:54:12 PCNAME kernel: [    2.972209] sas: ata7: end_device-1:0: dev error handler
/var/log/kern.log:Feb 14 16:54:12 PCNAME kernel: [    4.128479] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 14 16:54:27 PCNAME kernel: [   20.044923] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 15 10:08:41 PCNAME kernel: [    0.920569] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 15 10:08:41 PCNAME kernel: [    1.133700] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 15 10:08:41 PCNAME kernel: [    2.972303] sas: ata7: end_device-2:0: dev error handler
/var/log/kern.log:Feb 15 10:08:41 PCNAME kernel: [    3.444048] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 15 10:09:17 PCNAME kernel: [   39.438001] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 15 10:30:42 PCNAME kernel: [    0.920991] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 15 10:30:42 PCNAME kernel: [    1.137853] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 15 10:30:42 PCNAME kernel: [    2.972220] sas: ata7: end_device-4:0: dev error handler
/var/log/kern.log:Feb 15 10:30:42 PCNAME kernel: [    3.427212] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 15 10:31:21 PCNAME kernel: [   43.823674] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 15 10:34:23 PCNAME kernel: [    0.920518] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 15 10:34:23 PCNAME kernel: [    1.137636] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 15 10:34:23 PCNAME kernel: [    2.972190] sas: ata7: end_device-0:0: dev error handler
/var/log/kern.log:Feb 15 10:34:23 PCNAME kernel: [    3.646919] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 15 10:34:36 PCNAME kernel: [   17.193379] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 15 10:39:20 PCNAME kernel: [    0.920454] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 15 10:39:20 PCNAME kernel: [    1.137752] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 15 10:39:20 PCNAME kernel: [    2.972230] sas: ata7: end_device-2:0: dev error handler
/var/log/kern.log:Feb 15 10:39:20 PCNAME kernel: [    3.721900] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 15 10:39:30 PCNAME kernel: [   14.396325] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 15 10:55:52 PCNAME kernel: [    0.920612] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 15 10:55:52 PCNAME kernel: [    1.137655] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 15 10:55:52 PCNAME kernel: [    2.972301] sas: ata7: end_device-1:0: dev error handler
/var/log/kern.log:Feb 15 10:55:52 PCNAME kernel: [    3.437083] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 15 10:56:13 PCNAME kernel: [   25.140512] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 15 11:01:28 PCNAME kernel: [    0.924650] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 15 11:01:28 PCNAME kernel: [    1.137654] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 15 11:01:28 PCNAME kernel: [    2.972233] sas: ata7: end_device-0:0: dev error handler
/var/log/kern.log:Feb 15 11:01:28 PCNAME kernel: [    3.751045] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 15 11:01:37 PCNAME kernel: [   13.082269] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 15 11:03:27 PCNAME kernel: [    0.921358] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 15 11:03:27 PCNAME kernel: [    1.133827] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Feb 15 11:03:27 PCNAME kernel: [    2.972240] sas: ata7: end_device-0:0: dev error handler
/var/log/kern.log:Feb 15 11:03:27 PCNAME kernel: [    3.637013] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Feb 15 11:03:37 PCNAME kernel: [   14.055897] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Feb 15 11:25:19 PCNAME kernel: [    0.920833] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Feb 15 11:25:19 PCNAME kernel: [    1.137748] RAS: Correctable Errors collector initialized.
Binary file /var/log/kern.log matches
/var/log/syslog:Feb 15 10:14:17 PCNAME systemd-resolved[755]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced featur
e level UDP.
/var/log/syslog:Feb 15 10:14:17 PCNAME systemd-resolved[755]: message repeated 3 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying tra
nsaction with reduced feature level UDP.]
/var/log/syslog:Feb 15 10:25:10 PCNAME systemd-resolved[755]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced featur
e level UDP.
/var/log/syslog:Feb 15 10:25:49 PCNAME systemd-resolved[755]: message repeated 24 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying tr
ansaction with reduced feature level UDP.]
/var/log/syslog:Feb 15 10:26:56 PCNAME systemd-resolved[755]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced featur
e level UDP.
/var/log/syslog:Feb 15 10:30:42 PCNAME keyboard-setup.sh[398]: WARNING: Unknown X keysym "dead_belowmacron"
/var/log/syslog:Feb 15 10:30:42 PCNAME keyboard-setup.sh[398]: message repeated 3 times: [ WARNING: Unknown X keysym "dead_belowmacron"]
/var/log/syslog:Feb 15 10:30:42 PCNAME kernel: [    0.920991] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/syslog:Feb 15 10:30:42 PCNAME kernel: [    1.137853] RAS: Correctable Errors collector initialized.
/var/log/syslog:Feb 15 10:30:42 PCNAME kernel: [    2.972220] sas: ata7: end_device-4:0: dev error handler
/var/log/syslog:Feb 15 10:30:42 PCNAME kernel: [    3.427212] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Feb 15 10:30:42 PCNAME gpu-manager[839]: Error: can't open /lib/modules/4.15.0-45-generic/updates/dkms
/var/log/syslog:Feb 15 10:30:42 PCNAME gpu-manager[839]: Error: can't open /lib/modules/4.15.0-45-generic/updates/dkms
/var/log/syslog:Feb 15 10:30:42 PCNAME networkd-dispatcher[877]: WARNING: systemd-networkd is not running, output will be incomplete.
/var/log/syslog:Feb 15 10:30:43 PCNAME NetworkManager[878]: <warn>  [1550223043.0639] Error: failed to open /run/network/ifstate
/var/log/syslog:Feb 15 10:30:59 PCNAME sddm-greeter[1025]: qrc:///QtQuick/VirtualKeyboard/content/components/SelectionControl.qml:80: TypeError: Cannot read property 'cursorRectInterse
ctsClipRect' of null
/var/log/syslog:Feb 15 10:30:59 PCNAME sddm-greeter[1025]: qrc:///QtQuick/VirtualKeyboard/content/components/SelectionControl.qml:48: TypeError: Cannot read property 'anchorRectInterse
ctsClipRect' of null
/var/log/syslog:Feb 15 10:30:59 PCNAME sddm-greeter[1025]: qrc:///QtQuick/VirtualKeyboard/content/components/SelectionControl.qml:80: TypeError: Cannot read property 'cursorRectInterse
ctsClipRect' of null
/var/log/syslog:Feb 15 10:30:59 PCNAME sddm-greeter[1025]: qrc:///QtQuick/VirtualKeyboard/content/components/SelectionControl.qml:48: TypeError: Cannot read property 'anchorRectInterse
ctsClipRect' of null
/var/log/syslog:Feb 15 10:31:00 PCNAME org.kde.KScreen[1223]: kscreen.xcb.helper: Event Error:  147
/var/log/syslog:Feb 15 10:31:21 PCNAME kernel: [   43.823674] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/syslog:Feb 15 10:31:26 PCNAME pulseaudio[1361]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bl
uez': timed out (service_start_timeout=25000ms)
/var/log/syslog:Feb 15 10:34:23 PCNAME keyboard-setup.sh[414]: WARNING: Unknown X keysym "dead_belowmacron"
/var/log/syslog:Feb 15 10:34:23 PCNAME keyboard-setup.sh[414]: message repeated 3 times: [ WARNING: Unknown X keysym "dead_belowmacron"]
/var/log/syslog:Feb 15 10:34:23 PCNAME gpu-manager[858]: Error: can't open /lib/modules/4.15.0-45-generic/updates/dkms
/var/log/syslog:Feb 15 10:34:23 PCNAME gpu-manager[858]: Error: can't open /lib/modules/4.15.0-45-generic/updates/dkms
/var/log/syslog:Feb 15 10:34:23 PCNAME kernel: [    0.920518] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/syslog:Feb 15 10:34:23 PCNAME kernel: [    1.137636] RAS: Correctable Errors collector initialized.
/var/log/syslog:Feb 15 10:34:23 PCNAME kernel: [    2.972190] sas: ata7: end_device-0:0: dev error handler
/var/log/syslog:Feb 15 10:34:23 PCNAME kernel: [    3.646919] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Feb 15 10:34:23 PCNAME networkd-dispatcher[851]: WARNING: systemd-networkd is not running, output will be incomplete.
/var/log/syslog:Feb 15 10:34:24 PCNAME NetworkManager[902]: <warn>  [1550223264.3848] Error: failed to open /run/network/ifstate
/var/log/syslog:Feb 15 10:34:31 PCNAME sddm-greeter[1040]: qrc:///QtQuick/VirtualKeyboard/content/components/SelectionControl.qml:80: TypeError: Cannot read property 'cursorRectInterse
ctsClipRect' of null
/var/log/syslog:Feb 15 10:34:31 PCNAME sddm-greeter[1040]: qrc:///QtQuick/VirtualKeyboard/content/components/SelectionControl.qml:48: TypeError: Cannot read property 'anchorRectInterse
ctsClipRect' of null
/var/log/syslog:Feb 15 10:34:31 PCNAME sddm-greeter[1040]: qrc:///QtQuick/VirtualKeyboard/content/components/SelectionControl.qml:80: TypeError: Cannot read property 'cursorRectInterse
ctsClipRect' of null
/var/log/syslog:Feb 15 10:34:31 PCNAME sddm-greeter[1040]: qrc:///QtQuick/VirtualKeyboard/content/components/SelectionControl.qml:48: TypeError: Cannot read property 'anchorRectInterse
ctsClipRect' of null
/var/log/syslog:Feb 15 10:34:32 PCNAME org.kde.KScreen[1238]: kscreen.xcb.helper: Event Error:  147
Binary file /var/log/syslog matches
/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.



```

The last entry is from 10:34 but the last freeze happened at about 15:10, so apparently nothing was logged. Seeing some earlier errors containing ata7 and the device name of my only hard drive sda1, could this freezing again stem from the disk? Unfortunately the IT guy is on holiday today so I can't ask if he used a new drive or formatted the old one or whatever. But maybe this is some known Kubuntu quirk?

---

### Post by TheFu on 2019-02-15
Whenever the gui seems to freeze, I don't assume the entire OS is frozen, just the 1 program or the display subsystem. Check this by using ssh into the machine the next time it appears to freeze, then run 'top' to see how the system is doing.  Be certain to setup ssh access BEFORE you need it.  If you cannot ssh in while it is frozen, then that leads to the entire OS being locked up as a strong possibility.

Usually, when I've had slow response with a desktop, it is because that desktop is using all the RAM and all the virtual memory. The top command will show that, so will 'free -hm' and vmstat.  When memory gets fully utilized, slowing everything down is how our OSes let us know we've asked too much from it.  In general, a swap partition/file for a desktop should be 4.1GB in size unless you hibernate.

You still have disk and/or cable and/or hba controller problems to sort.

---

### Post by SeijiSensei on 2019-02-16
I'm guessing they didn't give you a new hard drive.

How much RAM does this machine have? Does it have swap?  As TheFu says, install openssh-server on the machine.  Then if it locks up you can log into it from another computer with SSH and see where the problem might be. Running "top" often helps a lot.

---

### Post by speedymcs on 2019-02-18
Many thanks, I'll try SSH. The machine has 32GB RAM and I wasn't running anything memory hungry, though I've run into swapping issues before and when that happened, everything froze, while now I can still move the cursor freely. So that makes me doubt it's a memory issue.

---

### Post by speedymcs on 2019-02-18
After a couple of hours of running fine, the display froze again (except for the mouse) when I started a python script in VS Code. I haven't been able to start it again. After a hard reset, I get to the Kubuntu login screen fine, but after logging in it gets stuck on the transition between load screen and desktop. I was monitoring with htop via SSH. Logging in was possible during all the freezes but at no point I saw excessive RAM or CPU usage. When freezing at login, the memory stays at about 600 MB and all 12 CPUs at nearly 0%. Some stuff still happens, e.g. I saw Dropbox starting.

E: I confirmed with the IT guy that it's a new SSD with a fresh Kubuntu that I got here.

---

### Post by TheFu on 2019-02-19
32G of RAM?  Are you sure that isn't storage space?
Basically, with 32 of RAM, you aren't going to run out ever on a desktop no matter what you do. I'm assuming you don't do ESRi stuff or run Windows.

I'm back to the "hardware fault" as the likely problem, but there seem to have been some kernel issues with odd interactions reported since April. Some file systems have been seeing issues with specific kernel, encryption, setups too.

Also, I'd run memtest for at least 3 passes to check that it isn't a memory issue.

If you were able to ssh in, that would lead me to think it is GPU driver as the likely issue. Check the X11 logs.

---


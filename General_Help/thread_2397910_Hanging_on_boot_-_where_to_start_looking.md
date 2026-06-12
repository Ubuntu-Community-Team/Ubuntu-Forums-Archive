---
title: "Hanging on boot - where to start looking ?"
date: 2018-08-04
forum: General Help
---

### Post by oygle on 2018-08-04
Over the last few weeks, this computer has been hanging on boot. I have also noticed over the last 6 to 9 months, that it is taking longer and longer to boot up. It used to be only a few seconds on the kubuntu screen, and now it is a few minutes.

Anyway, back to the hanging. It just sits there with the Kubuntu logo screen. Only a power down and reboot fixes it.

It certainly is not disk space and I think this quad processor has 8 Gb ram. Here is the hard drive

/dev/sda1   ext4  16.58 Gb  -  8.14 gb used
/dev/sda2   ext4  910 gb -  390 gb used

Can someone please advise where I can star looking in the log files.

---

### Post by Bashing-om on 2018-08-04
oygle; Well ....

> 
Only a power down and reboot fixes it.

That "power down" can leave the file system in an inconsistent state.
What shows - From a liveDVD/USB -:
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
```

sudo e2fsck -C0 -p -f -v /dev/sdXY

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
Run then:
```

sudo e2fsck -f -y -v /dev/sdXY

```
where the 'XY' for the device is per:
```

sudo fdisk -lu

```
where we seek the booting partition noted by the asterisk.

If still with issues, the boot log is obtained from systemd:
```

journalctl -b -0

```
for the current boot.

[INDENT][INDENT]My bit to try and help
[/INDENT][/INDENT]

---

### Post by oygle on 2018-08-04
> **Bashing-om said:**
> oygle; Well ....


That "power down" can leave the file system in an inconsistent state.

Thanks for those commands. I was just browsing and found this - [https://ubuntuforums.org/showthread.php?t=2378682&p=13715290#post13715290](https://ubuntuforums.org/showthread.php?t=2378682&p=13715290#post13715290)

```
egrep -i 'error|warn|fault|fatal|fail' /var/log/syslog
```

and did that for all 3 log files. Nothing output from dmesg, but the other 2 had log entries around the time it was hanging (I rebooted at 8:43 am ). I have attached the output .

If I go into partition manager, it says the smartstatus is good and no errors. Tried the command as you suggested ..

```
sudo fdisk -lu
```

> [sudo] password for ***********: 
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd5925537

Device     Boot    Start        End    Sectors   Size Id Type
/dev/sda1  *        2048   34762749   34760702  16.6G 83 Linux
/dev/sda2       34762750 1953523711 1918760962   915G  5 Extended
/dev/sda5       34762752   44527615    9764864   4.7G 82 Linux swap / Solaris
/dev/sda6       44529664 1953523711 1908994048 910.3G 83 Linux


---

### Post by oygle on 2018-08-04
I'm hesitant to run that **e2fsck** command ...

[https://askubuntu.com/questions/47953/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted](https://askubuntu.com/questions/47953/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted)

---

### Post by Bashing-om on 2018-08-05
> **oygle said:**
> I'm hesitant to run that **e2fsck** command ...

[https://askubuntu.com/questions/47953/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted](https://askubuntu.com/questions/47953/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted)

being careful here is prudent !
Note please that I did say " - From a liveDVD/USB -: " .
Thus the target - sda1 - is not mounted and in use.

[INDENT]careful is no accident [/INDENT]

---

### Post by oygle on 2018-08-05
> **Bashing-om said:**
> 
Note please that I did say " - From a liveDVD/USB -: " .
Thus the target - sda1 - is not mounted and in use.


Yes, thanks. I did take note of the first part - "live", but my knowledge did not extend to knowing if sda1 was mounted or not in a live boot situation.

I did the following ..

```
sudo touch /forcefsck
```

then a reboot, and

```
egrep -i 'fsck' /var/log/syslog
```

> Aug  5 08:43:41  systemd-fsck[714]: /dev/sda6: recovering journal
Aug  5 08:43:41  systemd-fsck[714]: /dev/sda6: clean, 252096/59662336 files, 94213204/238624256 blocks
Aug  5 12:17:44  systemd-fsck[682]: Please pass 'fsck.mode=force' on the kernel command line rather than creating /forcefsck on the root file system.
Aug  5 12:17:44  systemd-fsck[682]: /dev/sda6: 252103/59662336 files (0.5% non-contiguous), 94213420/238624256 blocks

---

### Post by oygle on 2018-08-05
The hanging only happens intermitently, but a reboot didn't fix it this time. Needed another reboot. Getting ridiculous and need to know why it is hanging.

I'd like to remove the splash screen permanently so I can see what is happening. Is this article correct on how to disable the splash screen ? - [http://dalvikplanet.blogspot.com/2018/05/how-to-disable-linux-kernel-boot-logo.html](http://dalvikplanet.blogspot.com/2018/05/how-to-disable-linux-kernel-boot-logo.html)

This is the contents of  ```
cat   /etc/default/grub
```

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"                                                                                                                                                                   
                                                                                                                                                                                                
# Uncomment to get a beep at grub start                                                                                                                                                         
#GRUB_INIT_TUNE="480 440 1"   

---

### Post by Bashing-om on 2018-08-05
oygle; Well ..

Running the file system check/repair from that live environment is the best practice here .
And Yes, I do want to see the boot messages, My grub file:
I have no issue with the above link instruction.
> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="priority=low"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

 where it is only needed to remove quiet splash from your line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
save the file and then run terminal command:
```

sudo update-grub

```
to propagate the change.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by oygle on 2018-08-05
> **Bashing-om said:**
> oygle; Well ..

Running the file system check/repair from that live environment is the best practice here .

Okay thanks, I'll chew on doing that.  :)

> **Bashing-om said:**
> 

And Yes, I do want to see the boot messages, My grub file:
I have no issue with the above link instruction.

 where it is only needed to remove quiet splash from your line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
save the file and then run terminal command:
```

sudo update-grub

```
to propagate the change.


Thanks for your help; I've now made the changes and run **sudo update-grub** to propagate the changes. So the next boot should tell me more. (Of course it didn't hang this morning, but it is intermitant).

---

### Post by oygle on 2018-08-06
Well, it hung this morning, but I have no idea what it was hanging on. That is because, that whilst the recent changes to the grub file enabled me to see all the boot entries with out the splash screen, as soon as the login screen appears, I can no longer view what is happening.

Should I uncomment this line, but then how to do I start up the 'splash' screen after a successful login with no hanging ?

> # Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

---

### Post by oygle on 2018-08-10
This problem **still** happens because I can't see what it is that is causing the hang. Had to boot up 3 times this morning. Reminds me of Windows.  :(

How do I stop the splash screen from displaying, post boot ?

---

### Post by Bashing-om on 2018-08-10
oygle; Well.

All I do is remove quiet splash from the grub file.
The boot log will be of interest here:
```

journalctl -b -0

```

[INDENT]best I can help
[/INDENT]

---

### Post by oygle on 2018-08-11
> **Bashing-om said:**
> All I do is remove quiet splash from the grub file.

Okay, I have done that. So, it seems I can't have a 'splash-less' post boot ?

> **Bashing-om said:**
> 
The boot log will be of interest here:
```

journalctl -b -0

```

If I have 2 boots, one that hangs and one that doesn't, will the above command only give me the 2nd boot entries ?

There were many entries 'highlighted', like bright white, and there were some red. Here are the red ones (but this is from a 'non hang boot):

> 
nouveau 0000:08:00.0: unknown chipset (118010a2)

bluetoothd[925]: Failed to obtain handles for "Service Changed" characteristic
 bluetoothd[925]: Not enough free handles to register service
 bluetoothd[925]: Error adding Link Loss service
 bluetoothd[925]: Not enough free handles to register service
 bluetoothd[925]: Not enough free handles to register service
 bluetoothd[925]: Not enough free handles to register service
 bluetoothd[925]: Current Time Service could not be registered
 bluetoothd[925]: gatt-time-server: Input/output error (5)
 bluetoothd[925]: Not enough free handles to register service
 bluetoothd[925]: Not enough free handles to register service
 bluetoothd[925]: Sap driver initialization failed.
 bluetoothd[925]: sap-server: Operation not permitted (1)

NetworkManager[903]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed



Thanks  :)

---

### Post by oygle on 2018-08-12
These are the last entries in syslog before the hang ..

> Aug 12 19:18:11 oygle rtkit-daemon[1631]: Supervising 1 threads of 1 processes of 1 users.
Aug 12 19:18:11 oygle rtkit-daemon[1631]: Successfully made thread 1660 of process 1630 (n/a) owned by '1000' RT at priority 5.
Aug 12 19:18:11 oygle rtkit-daemon[1631]: Supervising 2 threads of 1 processes of 1 users.
Aug 12 19:18:11 oygle rtkit-daemon[1631]: Supervising 2 threads of 1 processes of 1 users.
Aug 12 19:18:11 oygle rtkit-daemon[1631]: Successfully made thread 1662 of process 1630 (n/a) owned by '1000' RT at priority 5.
Aug 12 19:18:11 oygle rtkit-daemon[1631]: Supervising 3 threads of 1 processes of 1 users.
Aug 12 19:18:11 oygle rtkit-daemon[1631]: Supervising 3 threads of 1 processes of 1 users.
Aug 12 19:18:11 oygle rtkit-daemon[1631]: Successfully made thread 1663 of process 1630 (n/a) owned by '1000' RT at priority 5.
Aug 12 19:18:11 oygle rtkit-daemon[1631]: Supervising 4 threads of 1 processes of 1 users.
Aug 12 19:18:12 oygle bluetoothd[1131]: Endpoint registered: sender=:1.46 path=/MediaEndpoint/A2DPSource
Aug 12 19:18:12 oygle bluetoothd[1131]: Endpoint registered: sender=:1.46 path=/MediaEndpoint/A2DPSink
Aug 12 19:18:12 oygle pulseaudio[1630]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 12 19:18:13 oygle kernel: [   56.500034] Bluetooth: RFCOMM TTY layer initialized
Aug 12 19:18:13 oygle kernel: [   56.500042] Bluetooth: RFCOMM socket layer initialized
Aug 12 19:18:13 oygle kernel: [   56.500048] Bluetooth: RFCOMM ver 1.11
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: XRandR::setConfig
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: Requested screen size is QSize(1366, 768)
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: Needed CRTCs:  1
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: Actions to perform:
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Primary Output: true
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011#011Old: 0
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011#011New: 67
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Change Screen Size: false
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Disable outputs: false
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Change outputs: false
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Enable outputs: false
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: RRSetOutputPrimary
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011New primary: 67
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: XRandR::setConfig done!
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: RRotify_OutputChange
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Output:  67
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011CRTC:  63
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Mode:  71
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Rotation:  "Rotate_0"
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Connection:  "Connected"
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Subpixel Order:  0
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: RRScreenChangeNotify
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Window: 50331652
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Root: 251
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Rotation:  "Rotate_0"
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Size ID: 0
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Size:  1366 768
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011SizeMM:  361 203
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: RRotify_OutputChange
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Output:  67
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011CRTC:  63
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Mode:  71
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Rotation:  "Rotate_0"
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Connection:  "Connected"
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: #011Subpixel Order:  0
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: XRandROutput 67 update
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011m_connected: 0
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011m_crtc XRandRCrtc(0x1f88290)
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011CRTC: 63
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011MODE: 71
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Connection: 0
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Primary: true
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: Output 67 : connected = true , enabled = true
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: XRandROutput 67 update
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011m_connected: 0
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011m_crtc XRandRCrtc(0x1f88290)
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011CRTC: 63
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011MODE: 71
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Connection: 0
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: #011Primary: true
Aug 12 19:18:15 oygle org.kde.KScreen[1495]: kscreen.xrandr: Output 67 : connected = true , enabled = true
Aug 12 19:18:16 oygle org.kde.KScreen[1495]: kscreen.xrandr: Emitting configChanged()
Aug 12 19:18:16 oygle org.kde.KScreen[1495]: kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )
Aug 12 19:18:17 oygle org.kde.kdeconnect[1495]: kdeconnect.core: KdeConnect daemon starting
Aug 12 19:18:17 oygle org.kde.KScreen[1495]: kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )
Aug 12 19:18:17 oygle org.kde.KScreen[1495]: message repeated 3 times: [ kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )]
Aug 12 19:18:17 oygle org.kde.kdeconnect[1495]: kdeconnect.core: Broadcasting identity packet
Aug 12 19:18:17 oygle org.kde.kdeconnect[1495]: kdeconnect.core: KdeConnect daemon started
Aug 12 19:18:17 oygle org.kde.kdeconnect[1495]: kdeconnect.core: Sending onNetworkChange to  1  LinkProviders
Aug 12 19:18:17 oygle org.kde.kdeconnect[1495]: kdeconnect.core: Broadcasting identity packet
Aug 12 19:18:17 oygle org.kde.kuiserver[1495]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Aug 12 19:18:17 oygle org.kde.kuiserver[1495]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Aug 12 19:18:17 oygle org.kde.KScreen[1495]: kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )
Aug 12 19:18:17 oygle org.kde.KScreen[1495]: message repeated 3 times: [ kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )]
Aug 12 19:18:18 oygle dhclient[1247]: XMT: Info-Request on enp7s0, interval 28540ms.
Aug 12 19:18:19 oygle org.kde.KScreen[1495]: kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )
Aug 12 19:18:33 oygle org.kde.KScreen[1495]: message repeated 11 times: [ kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )]
Aug 12 19:18:34 oygle NetworkManager[888]: <warn>  [1534065514.6789] dhcp6 (enp7s0): request timed out
Aug 12 19:18:34 oygle NetworkManager[888]: <info>  [1534065514.6789] dhcp6 (enp7s0): state changed unknown -> timeout
Aug 12 19:18:34 oygle NetworkManager[888]: <info>  [1534065514.6797] dhcp6 (enp7s0): canceled DHCP transaction, DHCP client pid 1247
Aug 12 19:18:34 oygle NetworkManager[888]: <info>  [1534065514.6797] dhcp6 (enp7s0): state changed timeout -> done
Aug 12 19:18:35 oygle systemd[1]: Starting Stop ureadahead data collection...
Aug 12 19:18:35 oygle systemd[1]: Started Stop ureadahead data collection.
Aug 12 19:18:35 oygle systemd[1]: Stopped Read required files in advance.
Aug 12 19:18:35 oygle kernel: [   79.059317] [UFW BLOCK] IN=enp7s0 OUT= MAC=************* SRC=192.168.20.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Aug 12 19:18:36 oygle kernel: [   80.071301] [UFW BLOCK] IN=enp7s0 OUT= MAC=************* SRC=192.168.20.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Aug 12 19:19:20 oygle org.kde.KScreen[1495]: kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )
Aug 12 19:19:27 oygle org.kde.KScreen[1495]: message repeated 15 times: [ kscreen: Primary output changed from KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" ) to KScreen::Output(Id: 67 , Name: "eDP1" ) ( "eDP1" )]

and the output from this command

```
egrep -i 'error|warn|fault|fatal|fail' /var/log/
```

on 3 system files - syslog kern.log and dmesg

> 
Aug 12 19:17:35 oygle kernel: [    0.000000] MTRR default type: uncachable
Aug 12 19:17:35 oygle kernel: [    0.000032] pid_max: default: 32768 minimum: 301
Aug 12 19:17:35 oygle kernel: [    0.017270] Spectre V2 : Retpoline compiled kernel.  Defaulting IBRS to disabled<6>[    0.017273] Speculative Store Bypass: Vulnerable
Aug 12 19:17:35 oygle kernel: [    0.220363] NetLabel:  unlabeled traffic allowed by default
Aug 12 19:17:35 oygle kernel: [    0.258570] PCI: CLS 64 bytes, default 64
Aug 12 19:17:35 oygle kernel: [    0.736329] io scheduler deadline registered (default)
Aug 12 19:17:35 oygle kernel: [    0.981733] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 12 19:17:35 oygle kernel: [    0.981790] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 12 19:17:35 oygle kernel: [    0.982141] nouveau: probe of 0000:08:00.0 failed with error -12
Aug 12 19:17:35 oygle kernel: [    1.002930] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Aug 12 19:17:35 oygle kernel: [    1.002933] ACPI Error: Method parse/execution failed [\_SB.PCI0.RP05.PEGP.DD02._BCL] (Node ffff8802271fa5f0), AE_NOT_FOUND (20150930/psparse-542)
Aug 12 19:17:35 oygle kernel: [   14.367211] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 12 19:17:35 oygle gpu-manager[892]: Error: can't open /lib/modules/4.4.0-131-generic/updates/dkms
Aug 12 19:17:35 oygle gpu-manager[892]: Error: can't open /lib/modules/4.4.0-131-generic/updates/dkms
Aug 12 19:17:36 oygle gpu-manager[892]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Aug 12 19:17:37 oygle kernel: [   20.896997] usb 1-1.6: device descriptor read/64, error -110
Aug 12 19:17:37 oygle smartd[841]: Device: /dev/sda [SAT], SMART Prefailure Attribute: 3 Spin_Up_Time changed from 92 to 93
Aug 12 19:17:38 oygle thermald[894]: sysfs read failed constraint_0_max_power_uw
Aug 12 19:17:38 oygle thermald[894]: sysfs read failed max_brightness
Aug 12 19:17:39 oygle NetworkManager[888]: <info>  [1534065459.5459] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
Aug 12 19:17:40 oygle freshclam[916]: Sun Aug 12 19:17:40 2018 -> Reading CVD header (main.cvd): Sun Aug 12 19:17:40 2018 -> ^Can't get information about db.local.clamav.net: Temporary failure in name resolution
Aug 12 19:17:40 oygle NetworkManager[888]: <warn>  [1534065460.4108] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
Aug 12 19:17:40 oygle colord[1036]: (colord:1036): Cd-WARNING **: failed to get session [pid 911]: No such device or address
Aug 12 19:17:41 oygle NetworkManager[888]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Aug 12 19:17:41 oygle snapd[913]: 2018/08/12 19:17:41.709611 stateengine.go:101: state ensure error: Get [https://api.snapcraft.io/api/v1/snaps/sections:](https://api.snapcraft.io/api/v1/snaps/sections:) dial tcp: lookup api.snapcraft.io on [::1]:53: read udp [::1]:33661->[::1]:53: read: connection refused
Aug 12 19:17:41 oygle NetworkManager[888]: <warn>  [1534065461.7695] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 12 19:17:43 oygle bluetoothd[1131]: Failed to obtain handles for "Service Changed" characteristic
Aug 12 19:17:43 oygle bluetoothd[1131]: Error adding Link Loss service
Aug 12 19:17:43 oygle bluetoothd[1131]: gatt-time-server: Input/output error (5)
Aug 12 19:17:43 oygle bluetoothd[1131]: Sap driver initialization failed.
Aug 12 19:17:45 oygle freshclam[916]: Sun Aug 12 19:17:45 2018 -> Reading CVD header (main.cvd): Sun Aug 12 19:17:45 2018 -> ^Can't get information about db.local.clamav.net: Temporary failure in name resolution
Aug 12 19:17:45 oygle systemd[1174]: Reached target Default.
Aug 12 19:17:47 oygle NetworkManager[888]: <info>  [1534065467.9178] policy: set 'Wired connection 1' (enp7s0) as default for IPv4 routing and DNS
Aug 12 19:17:48 oygle dnsmasq[1197]: warning: no upstream servers configured
Aug 12 19:17:49 oygle NetworkManager[888]: <info>  [1534065469.8525] policy: set 'Wired connection 1' (enp7s0) as default for IPv6 routing and DNS
Aug 12 19:17:50 oygle whoopsie[1280]: [19:17:50] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Aug 12 19:17:53 oygle upowerd[1409]: (upowerd:1409): UPower-Linux-WARNING **: energy 32.560000 bigger than full 15.747200
Aug 12 19:18:01 oygle systemd[1435]: Reached target Default.
Aug 12 19:18:04 oygle org.a11y.Bus[1495]: ** (process:1537): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Aug 12 19:18:09 oygle org.freedesktop.Telepathy.AccountManager[1495]: (process:1605): accounts-glib-WARNING **: Error reading /usr/share/accounts/providers/ktp-generic.provider: Failed to open file '/usr/share/accounts/providers/ktp-generic.provider': Permission denied
Aug 12 19:18:11 oygle org.kde.KScreen[1495]: kscreen.xcb.helper: Event Error:  147
Aug 12 19:18:12 oygle pulseaudio[1630]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 12 19:18:34 oygle NetworkManager[888]: <warn>  [1534065514.6789] dhcp6 (enp7s0): request timed out
Aug 12 19:20:27 oygle systemd-udevd[450]: Process '/usr/sbin/alsactl -E HOME=/run/alsa restore 1' failed with exit code 99.
Aug 12 19:20:27 oygle gpu-manager[927]: Error: can't open /lib/modules/4.4.0-131-generic/updates/dkms
Aug 12 19:20:27 oygle gpu-manager[927]: Error: can't open /lib/modules/4.4.0-131-generic/updates/dkms
Aug 12 19:20:27 oygle gpu-manager[927]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Aug 12 19:20:27 oygle kernel: [    0.000000] MTRR default type: uncachable
Aug 12 19:20:27 oygle kernel: [    0.000031] pid_max: default: 32768 minimum: 301
Aug 12 19:20:27 oygle kernel: [    0.017274] Spectre V2 : Retpoline compiled kernel.  Defaulting IBRS to disabled<6>[    0.017278] Speculative Store Bypass: Vulnerable
Aug 12 19:20:27 oygle kernel: [    0.223932] NetLabel:  unlabeled traffic allowed by default
Aug 12 19:20:27 oygle kernel: [    0.258141] PCI: CLS 64 bytes, default 64
Aug 12 19:20:27 oygle kernel: [    0.735064] io scheduler deadline registered (default)
Aug 12 19:20:27 oygle kernel: [    0.985272] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 12 19:20:27 oygle kernel: [    0.985328] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 12 19:20:27 oygle kernel: [    0.985572] nouveau: probe of 0000:08:00.0 failed with error -12
Aug 12 19:20:27 oygle kernel: [    1.006944] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Aug 12 19:20:27 oygle kernel: [    1.006947] ACPI Error: Method parse/execution failed [\_SB.PCI0.RP05.PEGP.DD02._BCL] (Node ffff8802271fa5f0), AE_NOT_FOUND (20150930/psparse-542)
Aug 12 19:20:27 oygle kernel: [   16.144715] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 12 19:20:28 oygle smartd[907]: Device: /dev/sda [SAT], SMART Prefailure Attribute: 3 Spin_Up_Time changed from 93 to 92
Aug 12 19:20:28 oygle kernel: [   22.935447] usb 1-1.6: device descriptor read/64, error -110
Aug 12 19:20:28 oygle thermald[901]: sysfs read failed constraint_0_max_power_uw
Aug 12 19:20:28 oygle thermald[901]: sysfs read failed max_brightness
Aug 12 19:20:29 oygle NetworkManager[903]: <info>  [1534065629.7713] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
Aug 12 19:20:30 oygle NetworkManager[903]: <warn>  [1534065630.7795] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
Aug 12 19:20:31 oygle colord[1054]: (colord:1054): Cd-WARNING **: failed to get session [pid 864]: No such device or address
Aug 12 19:20:31 oygle NetworkManager[903]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Aug 12 19:20:31 oygle NetworkManager[903]: <warn>  [1534065631.6568] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 12 19:20:31 oygle freshclam[895]: Sun Aug 12 19:20:31 2018 -> Reading CVD header (main.cvd): Sun Aug 12 19:20:31 2018 -> ^Can't get information about db.local.clamav.net: Temporary failure in name resolution
Aug 12 19:20:33 oygle snapd[933]: 2018/08/12 19:20:33.460976 stateengine.go:101: state ensure error: Get [https://api.snapcraft.io/api/v1/snaps/sections:](https://api.snapcraft.io/api/v1/snaps/sections:) dial tcp: lookup api.snapcraft.io on [::1]:53: read udp [::1]:55145->[::1]:53: read: connection refused
Aug 12 19:20:35 oygle bluetoothd[1154]: Failed to obtain handles for "Service Changed" characteristic
Aug 12 19:20:35 oygle bluetoothd[1154]: Error adding Link Loss service
Aug 12 19:20:35 oygle bluetoothd[1154]: gatt-time-server: Input/output error (5)
Aug 12 19:20:35 oygle bluetoothd[1154]: Sap driver initialization failed.
Aug 12 19:20:35 oygle NetworkManager[903]: <info>  [1534065635.5269] policy: set 'Wired connection 1' (enp7s0) as default for IPv4 routing and DNS
Aug 12 19:20:35 oygle systemd[1177]: Reached target Default.
Aug 12 19:20:35 oygle dnsmasq[1175]: warning: no upstream servers configured
Aug 12 19:20:36 oygle freshclam[895]: Sun Aug 12 19:20:36 2018 -> Reading CVD header (main.cvd): Sun Aug 12 19:20:36 2018 -> ^Can't get information about db.local.clamav.net: Temporary failure in name resolution
Aug 12 19:20:38 oygle NetworkManager[903]: <info>  [1534065638.6757] policy: set 'Wired connection 1' (enp7s0) as default for IPv6 routing and DNS
Aug 12 19:20:40 oygle whoopsie[1374]: [19:20:40] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Aug 12 19:20:43 oygle upowerd[1419]: (upowerd:1419): UPower-Linux-WARNING **: energy 32.560000 bigger than full 15.747200
Aug 12 19:20:52 oygle systemd[1444]: Reached target Default.
Aug 12 19:20:55 oygle org.a11y.Bus[1503]: ** (process:1545): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Aug 12 19:20:59 oygle org.kde.KScreen[1503]: kscreen.xcb.helper: Event Error:  147
Aug 12 19:20:59 oygle org.freedesktop.Telepathy.AccountManager[1503]: (process:1605): accounts-glib-WARNING **: Error reading /usr/share/accounts/providers/ktp-generic.provider: Failed to open file '/usr/share/accounts/providers/ktp-generic.provider': Permission denied
Aug 12 19:21:02 oygle pulseaudio[1649]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 12 19:21:23 oygle NetworkManager[903]: <warn>  [1534065683.6690] dhcp6 (enp7s0): request timed out
Aug 12 19:17:35 oygle kernel: [    0.000000] MTRR default type: uncachable
Aug 12 19:17:35 oygle kernel: [    0.000032] pid_max: default: 32768 minimum: 301
Aug 12 19:17:35 oygle kernel: [    0.017270] Spectre V2 : Retpoline compiled kernel.  Defaulting IBRS to disabled<6>[    0.017273] Speculative Store Bypass: Vulnerable
Aug 12 19:17:35 oygle kernel: [    0.220363] NetLabel:  unlabeled traffic allowed by default
Aug 12 19:17:35 oygle kernel: [    0.258570] PCI: CLS 64 bytes, default 64
Aug 12 19:17:35 oygle kernel: [    0.736329] io scheduler deadline registered (default)
Aug 12 19:17:35 oygle kernel: [    0.981733] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 12 19:17:35 oygle kernel: [    0.981790] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 12 19:17:35 oygle kernel: [    0.982141] nouveau: probe of 0000:08:00.0 failed with error -12
Aug 12 19:17:35 oygle kernel: [    1.002930] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Aug 12 19:17:35 oygle kernel: [    1.002933] ACPI Error: Method parse/execution failed [\_SB.PCI0.RP05.PEGP.DD02._BCL] (Node ffff8802271fa5f0), AE_NOT_FOUND (20150930/psparse-542)
Aug 12 19:17:35 oygle kernel: [   14.367211] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 12 19:17:37 oygle kernel: [   20.896997] usb 1-1.6: device descriptor read/64, error -110
Aug 12 19:17:39 oygle NetworkManager[888]: <info>  [1534065459.5459] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
Aug 12 19:17:40 oygle NetworkManager[888]: <warn>  [1534065460.4108] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
Aug 12 19:17:41 oygle NetworkManager[888]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Aug 12 19:17:41 oygle NetworkManager[888]: <warn>  [1534065461.7695] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 12 19:17:47 oygle NetworkManager[888]: <info>  [1534065467.9178] policy: set 'Wired connection 1' (enp7s0) as default for IPv4 routing and DNS
Aug 12 19:17:49 oygle NetworkManager[888]: <info>  [1534065469.8525] policy: set 'Wired connection 1' (enp7s0) as default for IPv6 routing and DNS
Aug 12 19:18:34 oygle NetworkManager[888]: <warn>  [1534065514.6789] dhcp6 (enp7s0): request timed out
Aug 12 19:20:27 oygle kernel: [    0.000000] MTRR default type: uncachable
Aug 12 19:20:27 oygle kernel: [    0.000031] pid_max: default: 32768 minimum: 301
Aug 12 19:20:27 oygle kernel: [    0.017274] Spectre V2 : Retpoline compiled kernel.  Defaulting IBRS to disabled<6>[    0.017278] Speculative Store Bypass: Vulnerable
Aug 12 19:20:27 oygle kernel: [    0.223932] NetLabel:  unlabeled traffic allowed by default
Aug 12 19:20:27 oygle kernel: [    0.258141] PCI: CLS 64 bytes, default 64
Aug 12 19:20:27 oygle kernel: [    0.735064] io scheduler deadline registered (default)
Aug 12 19:20:27 oygle kernel: [    0.985272] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 12 19:20:27 oygle kernel: [    0.985328] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 12 19:20:27 oygle kernel: [    0.985572] nouveau: probe of 0000:08:00.0 failed with error -12
Aug 12 19:20:27 oygle kernel: [    1.006944] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Aug 12 19:20:27 oygle kernel: [    1.006947] ACPI Error: Method parse/execution failed [\_SB.PCI0.RP05.PEGP.DD02._BCL] (Node ffff8802271fa5f0), AE_NOT_FOUND (20150930/psparse-542)
Aug 12 19:20:27 oygle kernel: [   16.144715] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 12 19:20:28 oygle kernel: [   22.935447] usb 1-1.6: device descriptor read/64, error -110
Aug 12 19:20:29 oygle NetworkManager[903]: <info>  [1534065629.7713] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
Aug 12 19:20:30 oygle NetworkManager[903]: <warn>  [1534065630.7795] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
Aug 12 19:20:31 oygle NetworkManager[903]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Aug 12 19:20:31 oygle NetworkManager[903]: <warn>  [1534065631.6568] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 12 19:20:35 oygle NetworkManager[903]: <info>  [1534065635.5269] policy: set 'Wired connection 1' (enp7s0) as default for IPv4 routing and DNS
Aug 12 19:20:38 oygle NetworkManager[903]: <info>  [1534065638.6757] policy: set 'Wired connection 1' (enp7s0) as default for IPv6 routing and DNS
Aug 12 19:21:23 oygle NetworkManager[903]: <warn>  [1534065683.6690] dhcp6 (enp7s0): request timed out



---

### Post by kc1di on 2018-08-12
Lets find out what's taking the time to boot first.
in a terminal type this command and look at what is taking so much time.```
 systemd-analyze blame 
```
it will give you a list of the times it takes each item during the boot sequence. If the boot is hung the last item in the list may be a clue.

---

### Post by oygle on 2018-08-12
> **kc1di said:**
> Lets find out what's taking the time to boot first.
in a terminal type this command and look at what is taking so much time.```
 systemd-analyze blame 
```
it will give you a list of the times it takes each item during the boot sequence. If the boot is hung the last item in the list may be a clue.

Thanks, for some reason as I was listening to an audio, the screen went completely blank (although I could still hear the audio) and I couldn't get the screen back. Three reboots to get past 2 hangs.

```
systemd-analyze blame
```

> 11.987s dev-sda1.device
          9.698s mysql.service
          9.364s NetworkManager-wait-online.service
          9.083s ufw.service
          8.501s systemd-tmpfiles-setup-dev.service
          6.032s snapd.service
          3.714s NetworkManager.service
          3.436s accounts-daemon.service
          3.279s gpu-manager.service
          3.043s ModemManager.service
          3.043s grub-common.service
          1.797s thermald.service
          1.676s [email]systemd-fsck@dev-disk-by\x2duuid-1c65e969\x2d40a8\x2d4ce3\x2d8319\x2dc951f0a238be.servic[/email]e
          1.467s keyboard-setup.service
          1.381s ssh.service
          1.178s irqbalance.service
          1.038s apport.service
           981ms resolvconf.service
           838ms dev-hugepages.mount
           831ms bluetooth.service                                                                                                                                                              
           812ms networking.service                                                                                                                                                             
           786ms sys-kernel-debug.mount                                                                                                                                                         
           781ms systemd-logind.service                                                                                                                                                         
           773ms dev-mqueue.mount                                                                                                                                                               
           726ms ondemand.service                                                                                                                                                               
           708ms lm-sensors.service                                                                                                                                                             
           695ms alsa-restore.service                                                                                                                                                           
           685ms pppd-dns.service                                                                                                                                                               
           677ms rsyslog.service                                                                                                                                                                
           666ms systemd-user-sessions.service                                                                                                                                                  
           659ms avahi-daemon.service                                                                                                                                                           
           642ms colord.service                                                                                                                                                                 
           569ms polkitd.service                                                                                                                                                                
           513ms kmod-static-nodes.service                                                                                                                                                      
           506ms systemd-modules-load.service                                                                                                                                                   
           432ms apparmor.service                                                                                                                                                               
           385ms wpa_supplicant.service                                                                                                                                                         
           365ms console-setup.service
           312ms sys-fs-fuse-connections.mount
           291ms systemd-journald.service
           269ms upower.service
           197ms systemd-udev-trigger.service
           193ms binfmt-support.service
           192ms plymouth-read-write.service
           192ms systemd-rfkill.service
           179ms systemd-timesyncd.service
           174ms snapd.seeded.service
           160ms systemd-sysctl.service
           136ms systemd-tmpfiles-setup.service
           130ms systemd-udevd.service
            97ms [email]user@118.servic[/email]e
            86ms udisks2.service
            75ms systemd-journal-flush.service
            73ms home.mount
            73ms systemd-update-utmp.service
            54ms dev-disk-by\x2duuid-5dbe4cd4\x2d80c7\x2d411e\x2d8a30\x2dc47774ff14cc.swap
            45ms snapd.socket
            40ms systemd-remount-fs.service
            28ms setvtrgb.service
            18ms [email]user@1000.servic[/email]e
            18ms systemd-random-seed.service
            16ms hddtemp.service
            13ms apache2.service
            11ms plymouth-quit.service
             4ms proc-sys-fs-binfmt_misc.mount
             4ms ureadahead-stop.service
             3ms rtkit-daemon.service
             3ms systemd-update-utmp-runlevel.service
             3ms [email]systemd-backlight@backlight:intel_backlight.servic[/email]e
             3ms [email]systemd-backlight@leds:dell::kbd_backlight.servic[/email]e
             2ms rc-local.service
             2ms postfix.service
             2ms sddm.service

Starting from the bottom and working up ..

sddm.service - Simple Desktop Display Manager (SDDM) is a display manager (a graphical login program) for X11 and Wayland windowing systems
postfix.service - Postfix is the default Mail Transfer Agent (MTA) in Ubuntu
rc-local.service - ??
[email]systemd-backlight@leds:dell::kbd_backlight.servic[/email]e - I do have minor monitor probs , it won't stay on bright, and [https://ubuntuforums.org/showthread.php?t=2394672](https://ubuntuforums.org/showthread.php?t=2394672)

---

### Post by oygle on 2018-08-12
Before I do that fix, as I have also noticed the system waiting sometimes at BIOS, it might be wise to update the BIOS. An article at [https://www.dell.com/support/article/au/en/audhs1/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/au/en/audhs1/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)

---

### Post by Bashing-om on 2018-08-12
oygle; Hummm ...

Way over my skill set. But KDE as the desktop environment and I have to wonder if your hardware is affected:
 [https://www.phoronix.com/scan.php?page=news_item&px=Plasma-5.14-Fixes-CPU-Lock](https://www.phoronix.com/scan.php?page=news_item&px=Plasma-5.14-Fixes-CPU-Lock)

We get the other issues under control on this laptop, I have have a solution for the ACPI issues related in the log files.

What is the graphic's hardware:
```

sudo lshw -C display

```
and what is that graphic's situation:
```

/var/log/gpu-manager.log

```

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by oygle on 2018-08-13
> **Bashing-om said:**
> But KDE as the desktop environment and I have to wonder if your hardware is affected:
 [https://www.phoronix.com/scan.php?page=news_item&px=Plasma-5.14-Fixes-CPU-Lock](https://www.phoronix.com/scan.php?page=news_item&px=Plasma-5.14-Fixes-CPU-Lock)


Thanks, an interesting read.

```
sudo lshw -C display
```

> *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff

```
sudo  cat  /var/log/gpu-manager.log
```

> log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-131-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-131-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Vendor/Device Id: 8086:a16
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1341
BusID "PCI:8@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:08:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"                                                                                                                                                     
Skipping "/dev/dri/card0", driven by "i915"                                                                                                                                                     
Skipping "/dev/dri/card0", driven by "i915"                                                                                                                                                     
Found "/dev/dri/card0", driven by "i915"                                                                                                                                                        
output 0:                                                                                                                                                                                       
        card0-eDP-1                                                                                                                                                                             
Number of connected outputs for /dev/dri/card0: 1                                                                                                                                               
Does it require offloading? yes                                                                                                                                                                 
last cards number = 1                                                                                                                                                                           
Has amd? no                                                                                                                                                                                     
Has intel? yes                                                                                                                                                                                  
Has nvidia? no                                                                                                                                                                                  
How many cards? 1                                                                                                                                                                               
Has the system changed? No                                                                                                                                                                      
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu                                                                                                                                 
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf                                                                                                                                  
Current core alternative: (null)                                                                                                                                                                
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf                                                                                                                          
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? no
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? no
Is prime egl available? no
Single card detected
Nothing to do
No change - nothing to do

---

### Post by Bashing-om on 2018-08-13
oygle; Well !

We now know what one problem is:
> 

*-display UNCLAIMED
bk
product: GM108M [GeForce 840M]
bk
configuration: latency=0

where a driver for the graphics is not loaded.

show us what results:
```

sudo apt purge nvidia
sudo rm /etc/X11/xorg.conf
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```

[INDENT][INDENT]shedding light on the subject
[/INDENT][/INDENT]

---

### Post by oygle on 2018-08-13
> **Bashing-om said:**
> We now know what one problem is:

where a driver for the graphics is not loaded.

Okay, thanks for picking up that problem.

> **Bashing-om said:**
> 
show us what results:
```

sudo apt purge nvidia
sudo rm /etc/X11/xorg.conf
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```

Hmm, will the ```
sudo apt full-upgrade
``` upgrade the release of Kubuntu ? I have never used that command before. I did have a look at [https://askubuntu.com/questions/770135/apt-full-upgrade-versus-apt-get-dist-upgrade](https://askubuntu.com/questions/770135/apt-full-upgrade-versus-apt-get-dist-upgrade) , and ..

> full-upgrade (apt-get(8))
       full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.

So, it seems 'safe'. I just don't want a release upgrade, need to stay on 16.04.5 LTS for now.

I don't use nvidia and there is no file ' /etc/X11/xorg.conf' , but am okay to do those commands you suggested, as long as it won't upgrade me to the next release. I actually did backup all of /home yesterday to an external drive, though.  :D

---

### Post by Bashing-om on 2018-08-13
oygle; hey --- 

> 
 I just don't want a release upgrade, need to stay on 16.04.5 LTS for now.

'full-upgrade' only works on currently installed packages and will not do a release upgrade. That release upgrade is a different command.

> 
I don't use nvidia and there is no file ' /etc/X11/xorg.conf'

"product: GM108M [GeForce 840M]" shows that you do use Nvidia.
And for this hardware Nvidia recommends the 390.77 version driver.
[https://www.nvidia.com/Download/driverResults.aspx/136120/en-us](https://www.nvidia.com/Download/driverResults.aspx/136120/en-us)
 Now that driver is not in our software repo, so we try what the system will auto-install .. and if still graphic's issue we go get the 390.77 driver from our trusted PPA.

Yukkie if /etc/X11/xorg.conf fails to be created. This file is required in hybrid ( Intel - Nvida ) systems in order to be able to switch between the graphic's sets. We see what results when the proprietary driver installs.

Yeah just do it as posted above. Can not hurt and we see what happens.

[INDENT][INDENT]right, wrong - or otherwise
[INDENT][INDENT][INDENT]do something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2018-08-13
> **Bashing-om said:**
> 
'full-upgrade' only works on currently installed packages and will not do a release upgrade. That release upgrade is a different command.

Okay, will do those commands as you have listed then.  :)

> **Bashing-om said:**
> "product: GM108M [GeForce 840M]" shows that you do use Nvidia.
And for this hardware Nvidia recommends the 390.77 version driver.
[https://www.nvidia.com/Download/driverResults.aspx/136120/en-us](https://www.nvidia.com/Download/driverResults.aspx/136120/en-us)
 Now that driver is not in our software repo, so we try what the system will auto-install .. and if still graphic's issue we go get the 390.77 driver from our trusted PPA.

Sorry, my bad. I meant that I don't use the NVidia drivers.  :)

Here we go ....

 
```
sudo apt purge nvidia
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nvidia' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 24 not to upgrade.

```
sudo rm /etc/X11/xorg.conf
```

> rm: cannot remove '/etc/X11/xorg.conf': No such file or directory

```
sudo apt update
```

> Hit:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]                                                                                                                    
Get:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [320 kB]                                                                                                   
Get:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [236 kB]                                                                                        
Get:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [679 kB]                                                                                                    
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]                                                                                                                     
Hit:8 [http://ppa.launchpad.net/gabor-karsay/parlatype/ubuntu](http://ppa.launchpad.net/gabor-karsay/parlatype/ubuntu) xenial InRelease                                                                                                       
Get:9 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [619 kB]                                                                                                       
Get:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [274 kB]                                                                                                     
Ign:11 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 InRelease                                                                                                                                    
Get:12 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [247 kB]                                                                                            
Get:13 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [333 kB]                                                                             
Get:14 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,960 B]                                                                     
Get:15 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]                                                                       
Hit:16 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 Release                                                                                                                                         
Hit:17 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                                                                                                                                     
Hit:18 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) xenial InRelease                                                                                                                               
Hit:3 [https://nchc.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](https://nchc.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all InRelease                                                                                                             
Hit:20 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease                                                                                                                    
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [67.7 kB]                                                                                                   
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [68.0 kB]                                                                                                      
Get:23 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [107 kB]                                                                                                
Get:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [142 kB]                                                                                                   
Fetched 3,328 kB in 3s (953 kB/s)                                                                                                                                                               
Reading package lists... Done                                                                                                                                                                   
Building dependency tree                                                                                                                                                                        
Reading state information... Done                                                                                                                                                               
24 packages can be upgraded. Run 'apt list --upgradable' to see them.

```
sudo apt full-upgrade
```

> Reading package lists... Done                                                                                                                                                                   
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  fonts-opensymbol libreoffice-avmedia-backend-gstreamer libreoffice-base libreoffice-base-core libreoffice-base-drivers libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-impress libreoffice-java-common libreoffice-kde libreoffice-math libreoffice-pdfimport libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-style-breeze
  libreoffice-style-galaxy libreoffice-style-oxygen libreoffice-style-tango libreoffice-writer python3-uno uno-libs3 ure
24 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/80.6 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 235667 files and directories currently installed.)
Preparing to unpack .../libreoffice-java-common_1%3a5.1.6~rc2-0ubuntu1~xenial4_all.deb ...
Unpacking libreoffice-java-common (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../uno-libs3_5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking uno-libs3 (5.1.6~rc2-0ubuntu1~xenial4) over (5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../ure_5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking ure (5.1.6~rc2-0ubuntu1~xenial4) over (5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-calc_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-calc (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-impress_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-impress (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-draw_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-draw (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-kde_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-kde (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-writer_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-writer (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../python3-uno_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking python3-uno (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-sdbc-hsqldb_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-sdbc-hsqldb (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-sdbc-firebird_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-sdbc-firebird (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-style-oxygen_1%3a5.1.6~rc2-0ubuntu1~xenial4_all.deb ...
Unpacking libreoffice-style-oxygen (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-style-tango_1%3a5.1.6~rc2-0ubuntu1~xenial4_all.deb ...
Unpacking libreoffice-style-tango (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-style-galaxy_1%3a5.1.6~rc2-0ubuntu1~xenial4_all.deb ...
Unpacking libreoffice-style-galaxy (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-style-breeze_1%3a5.1.6~rc2-0ubuntu1~xenial4_all.deb ...
Unpacking libreoffice-style-breeze (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial4_all.deb ...
Unpacking libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-pdfimport_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-pdfimport (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-math_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-math (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-base-core_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-base-core (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-avmedia-backend-gstreamer_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-avmedia-backend-gstreamer (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-base_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-base (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-core_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-core (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../libreoffice-base-drivers_1%3a5.1.6~rc2-0ubuntu1~xenial4_amd64.deb ...
Unpacking libreoffice-base-drivers (1:5.1.6~rc2-0ubuntu1~xenial4) over (1:5.1.6~rc2-0ubuntu1~xenial3) ...
Preparing to unpack .../fonts-opensymbol_2%3a102.7+LibO5.1.6~rc2-0ubuntu1~xenial4_all.deb ...
Unpacking fonts-opensymbol (2:102.7+LibO5.1.6~rc2-0ubuntu1~xenial4) over (2:102.7+LibO5.1.6~rc2-0ubuntu1~xenial3) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-icon-theme (3.12.0-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1.1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.2) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Setting up uno-libs3 (5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up ure (5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up fonts-opensymbol (2:102.7+LibO5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
Setting up libreoffice-style-galaxy (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-style-tango (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-style-oxygen (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-style-breeze (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-java-common (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-core (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-base-core (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-calc (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-draw (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-impress (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-kde (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-writer (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up python3-uno (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-sdbc-hsqldb (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-sdbc-firebird (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-pdfimport (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-math (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-base-drivers (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Setting up libreoffice-base (1:5.1.6~rc2-0ubuntu1~xenial4) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...

```
sudo ubuntu-drivers autoinstall
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libcuda1-384 libjansson4 libxnvctrl0 nvidia-opencl-icd-384 nvidia-prime nvidia-settings ocl-icd-libopencl1 screen-resolution-extra
  xserver-xorg-legacy
Suggested packages:
  bumblebee
The following NEW packages will be installed:
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libcuda1-384 libjansson4 libxnvctrl0 nvidia-384 nvidia-opencl-icd-384 nvidia-prime nvidia-settings ocl-icd-libopencl1 screen-resolution-extra
  xserver-xorg-legacy
0 to upgrade, 14 to newly install, 0 to remove and 0 not to upgrade.
Need to get 84.2 MB of archives.
After this operation, 375 MB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 dkms all 2.2.0.3-2ubuntu11.5 [66.3 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-i386 amd64 2.23-0ubuntu10 [2,336 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 lib32gcc1 amd64 1:6.0.1-0ubuntu1 [46.6 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 xserver-xorg-legacy amd64 2:1.18.4-0ubuntu0.7 [35.9 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 nvidia-384 amd64 384.130-0ubuntu0.16.04.1 [73.7 MB]
Get:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 libcuda1-384 amd64 384.130-0ubuntu0.16.04.1 [3,702 kB]                                                               
Get:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libjansson4 amd64 2.7-3ubuntu0.1 [27.1 kB]                                                                                 
Get:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 libxnvctrl0 amd64 361.42-0ubuntu1 [11.2 kB]                                                                                        
Get:9 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 ocl-icd-libopencl1 amd64 2.2.8-1 [29.7 kB]                                                                                         
Get:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 nvidia-opencl-icd-384 amd64 384.130-0ubuntu0.16.04.1 [3,371 kB]                                                     
Get:11 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 bbswitch-dkms amd64 0.8-3ubuntu1 [11.6 kB]                                                                                        
Get:12 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 nvidia-prime amd64 0.8.2 [11.1 kB]                                                                                                
Get:13 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 screen-resolution-extra all 0.17.1.1~16.04.1 [11.7 kB]                                                                    
Get:14 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 nvidia-settings amd64 361.42-0ubuntu1 [855 kB]                                                                                    
Fetched 84.2 MB in 29s (2,859 kB/s)                                                                                                                                                            
Preconfiguring packages ...
Selecting previously unselected package dkms.
(Reading database ... 235667 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.5_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.5) ...
Selecting previously unselected package libc6-i386.
Preparing to unpack .../libc6-i386_2.23-0ubuntu10_amd64.deb ...
Unpacking libc6-i386 (2.23-0ubuntu10) ...
Replaced by files in installed package libc6:i386 (2.23-0ubuntu10) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a6.0.1-0ubuntu1_amd64.deb ...
Unpacking lib32gcc1 (1:6.0.1-0ubuntu1) ...
Selecting previously unselected package xserver-xorg-legacy.
Preparing to unpack .../xserver-xorg-legacy_2%3a1.18.4-0ubuntu0.7_amd64.deb ...
Unpacking xserver-xorg-legacy (2:1.18.4-0ubuntu0.7) ...
Selecting previously unselected package nvidia-384.
Preparing to unpack .../nvidia-384_384.130-0ubuntu0.16.04.1_amd64.deb ...
Unpacking nvidia-384 (384.130-0ubuntu0.16.04.1) ...
Selecting previously unselected package libcuda1-384.
Preparing to unpack .../libcuda1-384_384.130-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libcuda1-384 (384.130-0ubuntu0.16.04.1) ...
Selecting previously unselected package libjansson4:amd64.
Preparing to unpack .../libjansson4_2.7-3ubuntu0.1_amd64.deb ...
Unpacking libjansson4:amd64 (2.7-3ubuntu0.1) ...
Selecting previously unselected package libxnvctrl0.
Preparing to unpack .../libxnvctrl0_361.42-0ubuntu1_amd64.deb ...
Unpacking libxnvctrl0 (361.42-0ubuntu1) ...
Selecting previously unselected package ocl-icd-libopencl1:amd64.
Preparing to unpack .../ocl-icd-libopencl1_2.2.8-1_amd64.deb ...
Unpacking ocl-icd-libopencl1:amd64 (2.2.8-1) ...
Selecting previously unselected package nvidia-opencl-icd-384.
Preparing to unpack .../nvidia-opencl-icd-384_384.130-0ubuntu0.16.04.1_amd64.deb ...
Unpacking nvidia-opencl-icd-384 (384.130-0ubuntu0.16.04.1) ...
Selecting previously unselected package bbswitch-dkms.
Preparing to unpack .../bbswitch-dkms_0.8-3ubuntu1_amd64.deb ...
Unpacking bbswitch-dkms (0.8-3ubuntu1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.2_amd64.deb ...
Unpacking nvidia-prime (0.8.2) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1.1~16.04.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1.1~16.04.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_361.42-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (361.42-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up dkms (2.2.0.3-2ubuntu11.5) ...
Setting up libc6-i386 (2.23-0ubuntu10) ...
Setting up lib32gcc1 (1:6.0.1-0ubuntu1) ...
Setting up xserver-xorg-legacy (2:1.18.4-0ubuntu0.7) ...
Setting up nvidia-384 (384.130-0ubuntu0.16.04.1) ...
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-384/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-384
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 133) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-384-384.130 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-131-generic
Building for architecture x86_64
Building initial module for 4.4.0-131-generic
Done.

nvidia_384:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-131-generic/updates/dkms/

nvidia_384_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-131-generic/updates/dkms/

nvidia_384_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-131-generic/updates/dkms/

nvidia_384_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-131-generic/updates/dkms/

depmod.......

DKMS: install completed.
Setting up libcuda1-384 (384.130-0ubuntu0.16.04.1) ...
Setting up libjansson4:amd64 (2.7-3ubuntu0.1) ...
Setting up libxnvctrl0 (361.42-0ubuntu1) ...
Setting up ocl-icd-libopencl1:amd64 (2.2.8-1) ...
Setting up nvidia-opencl-icd-384 (384.130-0ubuntu0.16.04.1) ...
Setting up bbswitch-dkms (0.8-3ubuntu1) ...
Loading new bbswitch-0.8 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-131-generic
Building initial module for 4.4.0-131-generic
Done.

bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-131-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-prime (0.8.2) ...
Setting up screen-resolution-extra (0.17.1.1~16.04.1) ...
Setting up nvidia-settings (361.42-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for initramfs-tools (0.122ubuntu8.11) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-131-generic
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...

---

### Post by oygle on 2018-08-13
Rebooted - seems there are a lot of NVidia errors ..

> Aug 14 11:25:56 oygle sddm[1041]: Authentication error: "Process crashed"
Aug 14 11:25:56 oygle sddm[1041]: Authentication error: "Process crashed"
Aug 14 11:25:56 oygle org.kde.kglobalaccel[2014]: The X11 connection broke: I/O error (code 1)
Aug 14 11:25:56 oygle org.kde.kglobalaccel[2014]: XIO:  fatal IO error 6 (No such device or address) on X server ":0"
Aug 14 11:26:29 oygle systemd-udevd[384]: Process '/sbin/modprobe nvidia-modeset' failed with exit code 1.
Aug 14 11:26:29 oygle systemd-udevd[384]: Process '/sbin/modprobe nvidia-drm' failed with exit code 1.
Aug 14 11:26:29 oygle systemd-udevd[384]: Process '/sbin/modprobe nvidia-uvm' failed with exit code 1.
Aug 14 11:26:29 oygle systemd-udevd[441]: failed to execute '/usr/bin/nvidia-smi' '/usr/bin/nvidia-smi': No such file or directory
Aug 14 11:26:29 oygle systemd-udevd[384]: Process '/usr/bin/nvidia-smi' failed with exit code 2.
Aug 14 11:26:29 oygle systemd[875]: nvidia-persistenced.service: Failed at step EXEC spawning /usr/bin/nvidia-persistenced: No such file or directory
Aug 14 11:26:29 oygle kernel: [    0.000000] MTRR default type: uncachable
Aug 14 11:26:29 oygle kernel: [    0.000033] pid_max: default: 32768 minimum: 301
Aug 14 11:26:29 oygle kernel: [    0.017272] Spectre V2 : Retpoline compiled kernel.  Defaulting IBRS to disabled<6>[    0.017276] Speculative Store Bypass: Vulnerable
Aug 14 11:26:29 oygle kernel: [    0.219635] NetLabel:  unlabeled traffic allowed by default
Aug 14 11:26:29 oygle kernel: [    0.253835] PCI: CLS 64 bytes, default 64
Aug 14 11:26:29 oygle kernel: [    0.800958] io scheduler deadline registered (default)
Aug 14 11:26:29 oygle kernel: [    1.029567] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Aug 14 11:26:29 oygle kernel: [    1.080802] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Aug 14 11:26:29 oygle kernel: [    1.080806] ACPI Error: Method parse/execution failed [\_SB.PCI0.RP05.PEGP.DD02._BCL] (Node ffff8802271fa5f0), AE_NOT_FOUND (20150930/psparse-542)
Aug 14 11:26:29 oygle kernel: [    8.194138] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 14 11:26:29 oygle kernel: [   16.090572] usb 1-1.6: device descriptor read/64, error -110
Aug 14 11:26:31 oygle systemd[1]: Failed to start NVIDIA Persistence Daemon.
Aug 14 11:26:31 oygle systemd[1]: nvidia-persistenced.service: Unit entered failed state.
Aug 14 11:26:31 oygle systemd[1]: nvidia-persistenced.service: Failed with result 'exit-code'.
Aug 14 11:26:32 oygle thermald[923]: sysfs read failed constraint_0_max_power_uw
Aug 14 11:26:32 oygle thermald[923]: sysfs read failed max_brightness
Aug 14 11:26:34 oygle freshclam[855]: Tue Aug 14 11:26:34 2018 -> Reading CVD header (main.cvd): Tue Aug 14 11:26:34 2018 -> ^Can't get information about db.local.clamav.net: Temporary failure in name resolution
Aug 14 11:26:34 oygle gpu-manager[917]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Aug 14 11:26:35 oygle kernel: [   23.198549] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:36 oygle bluetoothd[1046]: Failed to obtain handles for "Service Changed" characteristic
Aug 14 11:26:36 oygle bluetoothd[1046]: Error adding Link Loss service
Aug 14 11:26:36 oygle bluetoothd[1046]: gatt-time-server: Input/output error (5)
Aug 14 11:26:36 oygle bluetoothd[1046]: Sap driver initialization failed.
Aug 14 11:26:36 oygle NetworkManager[940]: <info>  [1534209996.8595] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
Aug 14 11:26:38 oygle NetworkManager[940]: <warn>  [1534209998.7847] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
Aug 14 11:26:38 oygle snapd[942]: 2018/08/14 11:26:38.830044 stateengine.go:101: state ensure error: Get [https://api.snapcraft.io/api/v1/snaps/sections:](https://api.snapcraft.io/api/v1/snaps/sections:) dial tcp: lookup api.snapcraft.io on [::1]:53: read udp [::1]:60987->[::1]:53: read: connection refused
Aug 14 11:26:39 oygle freshclam[855]: Tue Aug 14 11:26:39 2018 -> Reading CVD header (main.cvd): Tue Aug 14 11:26:39 2018 -> ^Can't get information about db.local.clamav.net: Temporary failure in name resolution
Aug 14 11:26:39 oygle colord[1079]: (colord:1079): Cd-WARNING **: failed to get session [pid 925]: No such device or address
Aug 14 11:26:40 oygle NetworkManager[940]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Aug 14 11:26:41 oygle NetworkManager[940]: <warn>  [1534210001.2338] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 14 11:26:44 oygle freshclam[855]: Tue Aug 14 11:26:44 2018 -> Reading CVD header (main.cvd): Tue Aug 14 11:26:44 2018 -> ^Can't get information about db.local.clamav.net: Temporary failure in name resolution
Aug 14 11:26:44 oygle NetworkManager[940]: <info>  [1534210004.5206] policy: set 'Wired connection 1' (enp7s0) as default for IPv4 routing and DNS
Aug 14 11:26:44 oygle dnsmasq[1186]: warning: no upstream servers configured
Aug 14 11:26:47 oygle kernel: [   34.919972] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920030] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920067] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920102] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920137] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920185] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920219] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle NetworkManager[940]: <info>  [1534210007.5218] policy: set 'Wired connection 1' (enp7s0) as default for IPv6 routing and DNS
Aug 14 11:26:47 oygle kernel: [   34.934710] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:49 oygle whoopsie[1373]: [11:26:49] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Aug 14 11:26:51 oygle systemd[1461]: Reached target Default.
Aug 14 11:26:57 oygle upowerd[1484]: (upowerd:1484): UPower-Linux-WARNING **: energy 32.560000 bigger than full 15.747200
Aug 14 11:27:04 oygle systemd[1510]: Reached target Default.
Aug 14 11:27:09 oygle org.a11y.Bus[1569]: ** (process:1615): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Aug 14 11:27:13 oygle org.kde.KScreen[1569]: kscreen.xcb.helper: Event Error:  147
Aug 14 11:27:15 oygle org.freedesktop.Telepathy.AccountManager[1569]: (process:1675): accounts-glib-WARNING **: Error reading /usr/share/accounts/providers/ktp-generic.provider: Failed to open file '/usr/share/accounts/providers/ktp-generic.provider': Permission denied
Aug 14 11:27:21 oygle pulseaudio[1731]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 14 11:27:32 oygle NetworkManager[940]: <warn>  [1534210052.1354] dhcp6 (enp7s0): request timed out
Aug 14 11:27:34 oygle ureadahead[277]: ureadahead:.xsession-errors: Ignored relative path
Aug 14 11:27:34 oygle ureadahead[277]: ureadahead:.xsession-errors: Ignored relative path

Aug 14 11:25:56 oygle sddm[1041]: Authentication error: "Process crashed"
Aug 14 11:25:56 oygle sddm[1041]: Authentication error: "Process crashed"
Aug 14 11:26:29 oygle kernel: [    0.000000] MTRR default type: uncachable
Aug 14 11:26:29 oygle kernel: [    0.000033] pid_max: default: 32768 minimum: 301
Aug 14 11:26:29 oygle kernel: [    0.017272] Spectre V2 : Retpoline compiled kernel.  Defaulting IBRS to disabled<6>[    0.017276] Speculative Store Bypass: Vulnerable
Aug 14 11:26:29 oygle kernel: [    0.219635] NetLabel:  unlabeled traffic allowed by default
Aug 14 11:26:29 oygle kernel: [    0.253835] PCI: CLS 64 bytes, default 64
Aug 14 11:26:29 oygle kernel: [    0.800958] io scheduler deadline registered (default)
Aug 14 11:26:29 oygle kernel: [    1.029567] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Aug 14 11:26:29 oygle kernel: [    1.080802] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Aug 14 11:26:29 oygle kernel: [    1.080806] ACPI Error: Method parse/execution failed [\_SB.PCI0.RP05.PEGP.DD02._BCL] (Node ffff8802271fa5f0), AE_NOT_FOUND (20150930/psparse-542)
Aug 14 11:26:29 oygle kernel: [    8.194138] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 14 11:26:29 oygle kernel: [   16.090572] usb 1-1.6: device descriptor read/64, error -110
Aug 14 11:26:35 oygle kernel: [   23.198549] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:36 oygle NetworkManager[940]: <info>  [1534209996.8595] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
Aug 14 11:26:38 oygle NetworkManager[940]: <warn>  [1534209998.7847] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
Aug 14 11:26:40 oygle NetworkManager[940]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Aug 14 11:26:41 oygle NetworkManager[940]: <warn>  [1534210001.2338] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Aug 14 11:26:44 oygle NetworkManager[940]: <info>  [1534210004.5206] policy: set 'Wired connection 1' (enp7s0) as default for IPv4 routing and DNS
Aug 14 11:26:47 oygle kernel: [   34.919972] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920030] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920067] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920102] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920137] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920185] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle kernel: [   34.920219] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:26:47 oygle NetworkManager[940]: <info>  [1534210007.5218] policy: set 'Wired connection 1' (enp7s0) as default for IPv6 routing and DNS
Aug 14 11:26:47 oygle kernel: [   34.934710] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Aug 14 11:27:32 oygle NetworkManager[940]: <warn>  [1534210052.1354] dhcp6 (enp7s0): request timed out

---

### Post by Bashing-om on 2018-08-13
oygle; Yukkie -

Let's see of X tells us what is going on.
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]its broke, maw
[/INDENT][/INDENT]

---

### Post by oygle on 2018-08-13
Thanks for your help - [https://paste.ubuntu.com/p/qzBVpKNkD4/](https://paste.ubuntu.com/p/qzBVpKNkD4/)

---

### Post by Bashing-om on 2018-08-13
oygle; Humm ...

X is happy as can be;  nvidia driver installed with no issues per the log file.

Maybe we need to address those ACPI issues ??

Change the DSDT ( Differentiated Services Description Table) ?  instructions:
[http://iam.tj/prototype/enhancements/Windows-acpi_osi.html](http://iam.tj/prototype/enhancements/Windows-acpi_osi.html)


[INDENT][INDENT]just cause I do not know any better
[/INDENT][/INDENT]

---

### Post by oygle on 2018-08-14
> **Bashing-om said:**
> X is happy as can be;  nvidia driver installed with no issues per the log file.

That's good then, thanks.  :)

> **Bashing-om said:**
> 
Maybe we need to address those ACPI issues ??

Change the DSDT ( Differentiated Services Description Table) ?  instructions:
[http://iam.tj/prototype/enhancements/Windows-acpi_osi.html](http://iam.tj/prototype/enhancements/Windows-acpi_osi.html)


Thanks for that link. Maybe I should see how the laptop boots up in the next few days ? It has had one reboot with no hanging. Yes, the hanging was intermittent. I can just record each boot/reboot and if it hangs or not. Thanks "Bashing-om" , you have been a huge help.  :)

---

### Post by oygle on 2018-08-20
Well, it's been 7 days now,a nd with 1 reboot and then 14 consecutive boot ups, all with **NO** hanging, I can mark this as solved.

Thanks for your help "**Bashing-om**" and  "**kc1di**"  :)

---

### Post by Bashing-om on 2018-08-20
oygle; Great !

and
[INDENT][INDENT]Glad2help
[/INDENT][/INDENT]

---


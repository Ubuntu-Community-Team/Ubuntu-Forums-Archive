---
title: "USB stick automount not working"
date: 2013-05-01
forum: General Help
---

### Post by The Cog on 2013-05-01
I have just installed Xubuntu 13.04 for my Mum. Everything is sweet except that automount of her backup USB stick (VFAT) doesn't work. 

I would really like to be able to get automount working her backup stick, because re-training her to manually mount the stick will be difficult.

This is on xubuntu if that makes a difference. Under the Removable Storage settings, I have checked the three options:
    * Mount removable drives when hot-plugged
    * Mount removable media when inserted
    * Browse removable media when inserted

---

### Post by dino99 on 2013-05-01
can you check that issue with an other thumb ? (to know if its a hardware issue with that one only)

---

### Post by The Cog on 2013-05-01
Confirmed. I just tried two other sticks - an iso9900 (xubuntu live-cd/installer) and another stick with both a vfat and a btrfs partition. Neither automounted at all.
And there's nothing wrong with the backup stick - it mounts manually without any problem.

---

### Post by ajgreeny on 2013-05-01
Perhaps I'm grasping at straws, but have you tried all the other USB ports on the machine, or perhaps a powered USB hub, if you have one?

---

### Post by The Cog on 2013-05-01
Right - I've confirmed the behaviour on my laptop as well. Both behave the same. Strangely, the iso9900 installer stick does now automount on both machines, so maybe that was finger trouble earlier. But neither the vfat backup stick or my vfat+btrfs stick automount.

I'm also sure this is an Xubuntu issue - I found the settings for automount are stored in ~/.config/xfce4/xfconf/xfce-perchannel-xml/thunar-volman.xml.
It's 64-bit, if that's significant.

---

### Post by matt_symes on 2013-05-01
Hi 

@TheCog.

Is it creating the device file in /dev when you insert the stick ? 

If so that will discount udev and everything lower.

Kind regards

---

### Post by The Cog on 2013-05-01
Hi matt.

I believe so. **[FONT=Courier New]fdisk -l[/FONT]** shows it as /dev/sdb and /dev/sdb1 and I can mount the device manually with a mount command (mount /dev/sdb1 /mnt).

The partitions appear in gigolo, and in the devices side-panel of thunar. By clicking the device in either gigolo or thunar it mounts to /media/username/volumename. It just doesn't do it automatically when I plug the stick in.

---

### Post by matt_symes on 2013-05-01
Hi

That's rather odd. gvfs is used by Thunar for auto-mounting.

Plug in the device in but don't mount it using Thunar. What does this return ?

```
gvfs-mount --list
```

EDIT:

Does the pen drive have a label ?

Kind regards

---

### Post by The Cog on 2013-05-02
```
steve@dingly:~$ gvfs-mount --list
Drive(0): WDC WD1600BJKT-75F4T0
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
Drive(1): TEAC DVD-ROM DV28SV
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
Drive(2): Freecom DataBar USB2.0
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
  Volume(0): BackupStick
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
```
Drive 0 and 1 are there before I plug the stick in. Drive 2 appears after I plug the stick in. The vfat filesystem label is indeed BackupStick.

Looking at man gvfs-mount, I see that you can monitor events, so I did. This is the result:
```
steve@dingly:~$ gvfs-mount --monitor --detail
Monitoring events. Press Ctrl+C to quit.
Drive connected:    'Freecom DataBar USB2.0'
  Drive(0): Freecom DataBar USB2.0
    Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
    ids:
     unix-device: '/dev/sdb'
    themed icons:  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
    symbolic themed icons:  [drive-removable-media-usb-symbolic]  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
    is_media_removable=1
    has_media=1
    is_media_check_automatic=1
    can_poll_for_media=0
    can_eject=1
    can_start=0
    can_stop=0
    start_stop_type=shutdown
    sort_key=01hotplug/1367492865053959
    Volume(0): BackupStick
      Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
      ids:
       class: 'device'
       unix-device: '/dev/sdb1'
       uuid: 'C2F8-4274'
       label: 'BackupStick'
      themed icons:  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
      symbolic themed icons:  [drive-removable-media-usb-symbolic]  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
      can_mount=1
      can_eject=1
      should_automount=1
      sort_key=gvfs.time_detected_usec.1367492865156872

Volume added:       'BackupStick'
  Volume(0): BackupStick
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
    ids:
     class: 'device'
     unix-device: '/dev/sdb1'
     uuid: 'C2F8-4274'
     label: 'BackupStick'
    themed icons:  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
    symbolic themed icons:  [drive-removable-media-usb-symbolic]  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
    can_mount=1
    can_eject=1
    should_automount=1
    sort_key=gvfs.time_detected_usec.1367492865156872

```and then when I use gigolo to mount the drive it adds these lines:
```
Volume changed:     'BackupStick'
  Volume(0): BackupStick
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
    ids:
     class: 'device'
     unix-device: '/dev/sdb1'
     uuid: 'C2F8-4274'
     label: 'BackupStick'
    themed icons:  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
    symbolic themed icons:  [drive-removable-media-usb-symbolic]  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
    can_mount=1
    can_eject=1
    should_automount=1
    sort_key=gvfs.time_detected_usec.1367492865156872

Mount added: 'BackupStick'
  Mount(0): BackupStick -> file:///media/steve/BackupStick
    Type: GProxyMount (GProxyVolumeMonitorUDisks2)
    default_location=file:///media/steve/BackupStickRemovable Dr
    themed icons:  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
    symbolic themed icons:  [drive-removable-media-usb-symbolic]  [drive-removable-media-usb]  [drive-removable-media]  [drive-removable]  [drive]
    can_unmount=1
    can_eject=1
    is_shadowed=0
    sort_key=gvfs.time_detected_usec.1367492932314002

```
I notice that it says should_automount=1. 
Edit: It says that even if I change the configuration (in Settings Manager |  Removable Drives and Media) to not automount.

---

### Post by matt_symes on 2013-05-02
Hi

This is an odd one TheCog. So far that all looks fine and is what i would expect. 

This is what i find really odd.

> Right - I've confirmed the behaviour on my laptop as well. Both behave  the same. Strangely, the iso9900 installer stick does now automount on  both machines, so maybe that was finger trouble earlier. But neither the  vfat backup stick or my vfat+btrfs stick automount.

It'll mount some sticks and not others. I wonder if it's a known bug or something.

As it auto-mounts some devices, i would expect you to already be a member of the plugdev group.

It looks like the issue is either with udisks2, gvfs or thunar volume manger, although thunar volume manager does not explain gigolo.

It does not look like a policykit issue either.

I'm doing some research as well on this.

Kind regards

---

### Post by matt_symes on 2013-05-02
Hi

Anything in ~/.xession-errors when you plug the device in ?

```
tail -f ~/.xsession-errors
```

Plug the device in.  

BTW, I get this even when a volume  is auto-mounted correctly so this can probably be ignored.

> thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unknown block device type.

Kind regards

---

### Post by The Cog on 2013-05-02
I get this:
```
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unknown block device type.
thunar-volman: Could not detect the volume corresponding to the device.
```
With the stick that has both vfat and btrfs partitions, I get this:
```
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unknown block device type.
thunar-volman: Could not detect the volume corresponding to the device.
thunar-volman: Could not detect the volume corresponding to the device.

```This second listing is exactly the same as I get when I insert the installer stick (which does automount).

Are you not getting the same behaviour?

EDIT:
I just got a netbook working with Xubuntu 13.04 (32-bit) and automount works OK in that - the same stick that I've been trying on both these 64-bit machines.
So I think the problem is specifically with 64-bit Xubuntu. I ran the installer and did a check CD for integrity and it passed OK.

---

### Post by matt_symes on 2013-05-02
Hi

This is what i'm seeing...

> thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unknown block device type.


...but i does automount. 

I'm on 64bit Xubuntu as well - currently saucy - but i did not have the problem you are having in raring (not that i noticed anyway).

This is what i'm not getting...

> thunar-volman: Could not detect the volume corresponding to the device.

May be an idea to trawl through Launchpad looking for bug reports.

Kind regards

---

### Post by The Cog on 2013-05-02
Can't find anything on launchpad.

I have discovered more though. The problem exists with the live CD and varies with the hardware. Using the same live-CD installer (32-bit, created by using dd to write the iso to the installer stick). I boot the live CD, choose to try xubuntu, then when everything has settled down, insert the fat stick. On my netbook, the fat stick automounts, but on the laptop the fat stick fails to automount. So it's not just 64-bit but it seems hardware dependent.

Also, on my laptop, it does occasionally automount - about 1 time in ten. I just kept on plugging and unplugging the stick. I notice that in ~/.xsession-errors, when automount fails I get 
```
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Could not detect the volume corresponding to the device.
thunar-volman: Could not detect the volume corresponding to the device.
```
but on the occasions where it automounts, I don't get the second "Could not detect volume...". 
So it is both hardware dependent and intermittent. I wonder if it is a race condition somewhere and the slower hardware on my nebook means it always works there.

Also, after googling for the "Could not detect volume" message, I found a suggestion to run "dbus-launch thunar". I find that on my laptop, as long as that dbus-launched thunar window/process exists, the stick automounts 100% of the time. But when I close that thunar window, it reverts to only occasional automounting.

---

### Post by matt_symes on 2013-05-02
Hi

> I wonder if it is a race condition somewhere and the slower hardware on my nebook means it always works there.

Interesting. This may well be the problem.

> Also, after googling for the "Could not detect volume" message, I found a  suggestion to run "dbus-launch thunar". I find that on my laptop, as  long as that dbus-launched thunar window/process exists, the stick  automounts 100% of the time. But when I close that thunar window, it  reverts to only occasional automounting.

Maybe the issue is a dbus issue that is timing out after getting no response or something like that - that is speculation though. 

GVolumeMonitorUdisks2 uses dbus  to communicate with disks; org.freedesktop.UDisks2 and also uses dbus to communicate with thunar.

That may be worth looking.

On thing you may want to try is to eliminate udisks. From the terminal

```
sudo /usr/lib/udisks2/udisksd --replace
```

Insert and remove pendrive with and without thunar started via dbus launch and see what is displayed in the terminal.

Anything in the log files ?

**EDIT:**

As a sanity test can you post the output of this command without the stick plugged in and with no instances of Thunar running

```
ps aux | grep udisks
```

Kind regards

---

### Post by The Cog on 2013-05-02
That makes it rather more reliable, maybe 8/10 success rate. Here's the good and bad log output. 
```
Good:
19:31:53.279:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host88 [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:31:54.242:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host88/target88:0:0 [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:31:54.243:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host88/target88:0:0/88:0:0:0 [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:31:54.338:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host88/target88:0:0/88:0:0:0/block/sdb [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:31:54.406:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host88/target88:0:0/88:0:0:0/block/sdb/sdb1 [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:31:54.481:[9041]:[NOTICE]: Mounted /dev/sdb1 at /media/steve/BackupStick on behalf of uid 1000 [udiskslinuxfilesystem.c:1493, handle_mount()]

Bad:
19:35:09.900:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host98 [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:35:10.862:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host98/target98:0:0 [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:35:10.863:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host98/target98:0:0/98:0:0:0 [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:35:10.954:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host98/target98:0:0/98:0:0:0/block/sdb [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
19:35:11.017:[9007]:[DEBUG]: uevent add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host98/target98:0:0/98:0:0:0/block/sdb/sdb1 [udiskslinuxprovider.c:902, udisks_linux_provider_handle_uevent()]
```
Here's the rub though: To get rid of the console window, I put the process into the background and disowned it, then closed the window. The success-rate dropped again. It seems that having its debug output sent to the screen affects the race condition. 

So then I tried setting the niceness of udisksd to +5 and see if that helped, but it didn't.

For the ps -aux, I'm going to reboot for a clean session. I'll edit this post when I'm back.
EDIT: 
After a clean reboot:
```
steve@dingly:~$ ps aux | grep udisks
steve     2256  0.0  0.1 227552  6048 ?        Sl   19:55   0:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
root      2270  0.1  0.1 373172  6132 ?        Sl   19:55   0:00 /usr/lib/udisks2/udisksd --no-debug
steve     2515  0.0  0.0  16624   948 pts/0    S+   19:56   0:00 grep --color=auto udisks
```
but before the reboot, there were several instances of udisksd and volume-monitor running. It seems that --replace doesn't kill the previous usidksd. I don't know how the other volume monitors got started.

---

### Post by matt_symes on 2013-05-02
Hi

Well the symptom is obviously that udisks2 is not mounting the device. This may be a software bug.

Interesting that it should work better when writing to the console though. 

It seems to have been a common bug as well.

Out of interest can you post the output of

```
sudo lshw
```

It'll be interesting to see the hardware that is on the lappy.

Kind regards

---

### Post by The Cog on 2013-05-02
The easiest one for me to work on is this one - a Dell Latitude E5500: [http://pastebin.com/J6F1yZDh](http://pastebin.com/J6F1yZDh)

---

### Post by matt_symes on 2013-05-02
Hi

From the terminal and without the device plugged in...

```
/usr/lib/gvfs/gvfs-udisks2-volume-monitor
```

Plug the device in.

What output do you get when the device is recognised and not ?

I still think your right about some kind of race condition. It certainly looks like it may be that.

Kind regards

---

### Post by The Cog on 2013-05-03
You're going really deep into this, aren't you. I hope I'm not being a nuisance.

Not recognised:
```
### debug: in handle_supported
### debug: Name owner ':1.63' vanished
### debug: in handle_list
### debug: in handle_supported
### debug: Name owner ':1.66' vanished
### debug: in handle_list
### debug: in handle_supported
### debug: Name owner ':1.69' vanished
### debug: in handle_list
### debug: in handle_supported
### debug: Name owner ':1.72' vanished
### debug: in handle_list
### debug: emit_signal: 0x1c47a20
### debug: emit_signal: 0x1c47a20
### debug: emit_signal: 0x1c2fb30

```
Recognised:
```
### debug: in handle_supported
### debug: Name owner ':1.99' vanished
### debug: in handle_list
### debug: in handle_supported
### debug: Name owner ':1.102' vanished
### debug: in handle_list
### debug: in handle_supported
### debug: Name owner ':1.105' vanished
### debug: in handle_list
### debug: in handle_supported
### debug: Name owner ':1.108' vanished
### debug: in handle_list
### debug: emit_signal: 0x1c47ba0
### debug: emit_signal: 0x1c47ba0
### debug: emit_signal: 0x1c2fd10
### debug: in handle_volume_mount
### debug: emit_signal: 0x1c2fd10
### debug: emit_signal: 0x1c8a910
### debug: in volume_mount_cb
### debug:  success
### debug: in handle_supported
### debug: in handle_list
### debug: in handle_supported
### debug: in handle_list

```

---

### Post by matt_symes on 2013-05-04
Hi TheCog.

I'm still looking into this but i currently have the flu so progress is very slow.

I have not had many problems with my installs. Things just tend to work so it's nice to get my teeth into a problem.

Seeing if i can see any work around.

Kind regards

---

### Post by The Cog on 2013-05-04
Urgh. I hope you get over the flu quickly.

I'm glad you like getting stuck into a problem, but don't put yourself out on my account. 

Another snippet of info - I found a different USB stick, that seems to mount quite reliably on that laptop - 10/10 tries. 
So automount reliability changes with the same stick in different computers, and with different sticks in the same computer. It really, really feels like a timing issue/race condition. 

Your avatar keeps looking at me in a rather disturbing way.

---

### Post by matt_symes on 2013-05-08
Hi

I'm wondering if this is not a dbus issue. 

Not sure if your still having the problem but if you are it may be worth monitoring the dbus messages.

If you open a terminal and type

```
cd && dbus-monitor > dbus_gvfs.txt 2>&1
```

Plug the device in and wait 10 seconds or so.

You may then want to post the file dbus_gvfs.txt.

It looks like a messages are getting sent but not received somewhere or they are not getting sent due to some condition.

Kind regards

---

### Post by The Cog on 2013-05-09
I ran dbus-monitor and captured both a good and a bad insert. These are the two files:
    Good insert: [http://pastebin.com/syxExBD2](http://pastebin.com/syxExBD2)
    Failed insert: [http://pastebin.com/aWeiGBDQ](http://pastebin.com/aWeiGBDQ)

In both cases, I waited until gigolo showed the drive, then stopped the trace before unplugging the stick. When the automount works, gigolo shows a tick in the connected checkbox.

I compared the files using meld, and can see what may be some significant differences. 
Lines 1709-1715, a couple of method calls happen in a different order.
Line 2217, lots of stuff happens in the bad trace that doesn't happen in the good trace.
Line 2321(good)/2399(bad), lots of stuff happening in the good trace that doesn't happen in the bad one.

A great deal of the stuff at 2217 in the bad trace happens later (2321) in the good trace, so again, things are largely the same but in a different order.
I guess the devil is in the detail, and I'm not really sure what I'm looking for.

The 2>&1 wasn't needed. When I did "dbus-monitor > /dev/null", no error messages appeared on the screen while inserting/removing the stick.

---

### Post by khelms on 2013-05-22
I had the same problem with Xubuntu 12.04.   The thumb drive would show up under /dev/sdc1, but would not automount.   I tried the command listed here - gvfs-mount --list and got a message that it wasn't installed and I could get it by installing gvfs-bin.   I did an apt-get on that package and it also installed gvfs gvfs-common gvfs-daemons and gvfs-libs.   Once those packages were installed, I pulled the thumb drive out, put it back in, and voila, it automounted!

I think I removed some gvfs stuff a while back to resolve a bug where Thunar was extremely slow to open the first time and opened a second window when started.  I'll have to see if that problem is back now.

---

### Post by bkline on 2013-09-10
There is a bug report which looks like it matches this problem:

[https://bugs.launchpad.net/ubuntu/+source/thunar-volman/+bug/1090974](https://bugs.launchpad.net/ubuntu/+source/thunar-volman/+bug/1090974)

A workaround is included in the comments, but that workaround is reported to be effective only with pre-13.04 releases.

---

### Post by VMC on 2013-09-10
Or this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1207934").

---

### Post by r_mano on 2013-11-03
I have the same problem --- but worst, it normally doesn't automount anything.  Try all the possible workaround. I have opened a bug here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1241811](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1241811)

---

### Post by 5phinX on 2014-01-13
Hello, I had the same issue. No drive or partition was mounting automatically on xubuntu. My problem was solved by running xfce4-settings-editor,navigating to thunar-volman and changing options automount-drives/enabled and automount-media/enabled to true. Maybe give it a try.

---


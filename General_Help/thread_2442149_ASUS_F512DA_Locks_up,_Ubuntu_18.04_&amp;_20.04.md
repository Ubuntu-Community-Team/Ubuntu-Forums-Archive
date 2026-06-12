---
title: "ASUS F512DA Locks up, Ubuntu 18.04 &amp; 20.04"
date: 2020-04-30
forum: General Help
---

### Post by gabo4au on 2020-04-30
I recently purchased a new ASUS F512DA, with 4G RAM (awaiting shipment of 8G more), SSD, AMD Ryzen 3 3200U with Radeon Vega Mobile Gfx. 

I originally installed 18.04 LTS. From the start, it locked up about 2-3 times per day. Just becoming unresponsive while doing basic web surfing using Firefox. I typically also have Thunderbird email loaded and maybe a Libreoffice document or evince PDF loaded.

The lockups would happen more frequently after closing the lid and suspending over night. But not always after initially opening, but generally within an hour of working after opening. 

Since it's a new PC, I figured there was some hardware that was relatively new that had some bugs/issues (still could be the case), so I just lived with it and updated everything on a daily basis hoping it would resolve. 

When 20.04 LTS was released, I did an upgrade to that, hoping that would fix it as well. However, it did not and the locked are persisting. 

Scouring the logs, the only thing in syslog are lots of "tracker-extract" logs, nothing appears to be out of order (wish I knew how to reduce the tracker logging). There doesn't appear to be anything of note in kern.log or anywhere else I can find.

I'm a long time Linux user, various flavors, and I never thought I would come to a time where I was considering going to win 10. But this is ridiculous, especially in 2020. Lockups all day every day, I feel like I'm back to windows 386! :)

Any advice would be great. 

Thanks, gabo

---

### Post by dino99 on 2020-04-30
To find warning/error, glance at 'journalctl -b' output into a terminal
Locks are often related to the video driver: which one is installed/used, from which source ? 
Be sure first that each chipset/hardware is well identified.

Maybe try cleaning the system via bleachbit (as root, carefully select the features)
With recent hardware, always install recent kernel to get full support and adapted driver.

---

### Post by gabo4au on 2020-04-30
Thanks dino, that command gives many pages of info, not sure what I'm looking for. However, I did take note of the errors, etc that I see in there and will try to sort through all of them to see if I can figure something out. 

Regarding the video. I'm not real sure what driver "should" be loaded, but here is some info on the video.

lspci shows this for the video:
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev c4)

Here's everything from this command.

 sudo journalctl -b | grep -i video
 kernel: ACPI: Added _OSI(Linux-Dell-Video)
 kernel: ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
 kernel: input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:13/LNXVIDEO:01/input/input5
 kernel: videodev: Linux video capture interface: v2.00
 kernel: uvcvideo: Found UVC 1.50 device USB2.0 HD UVC WebCam (13d3:56dc)
 kernel: uvcvideo: Failed to initialize entity for entity 6
 kernel: uvcvideo: Failed to register entities (-22).
 kernel: usbcore: registered new interface driver uvcvideo
 kernel: USB Video Class driver (1.1.1)
 systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:acpi_video0...
 systemd-backlight[775]: Failed to get backlight or LED device 'backlight:acpi_video0': No such device
 systemd[1]: [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e: Main process exited, code=exited, status=1/FAILURE
 systemd[1]: [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e: Failed with result 'exit-code'.
 systemd[1]: Failed to start Load/Save Screen Backlight Brightness of backlight:acpi_video0.
 tracker-miner-f[1070]: Unable to get XDG user directory path for special directory &VIDEOS. Ignoring this location.
 tracker-miner-f[1070]: Unable to get XDG user directory path for special directory &VIDEOS. Ignoring this location.
 /usr/lib/gdm3/gdm-x-session[1966]:         X.Org Video Driver: 24.1
 /usr/lib/gdm3/gdm-x-session[1966]:         Module class: X.Org Video Driver
 /usr/lib/gdm3/gdm-x-session[1966]:         ABI class: X.Org Video Driver, version 24.0
 /usr/lib/gdm3/gdm-x-session[1966]:         Module class: X.Org Video Driver
 /usr/lib/gdm3/gdm-x-session[1966]:         ABI class: X.Org Video Driver, version 24.0
 /usr/lib/gdm3/gdm-x-session[1966]:         Module class: X.Org Video Driver
 /usr/lib/gdm3/gdm-x-session[1966]:         ABI class: X.Org Video Driver, version 24.1
 /usr/lib/gdm3/gdm-x-session[1966]:         Module class: X.Org Video Driver
 /usr/lib/gdm3/gdm-x-session[1966]:         ABI class: X.Org Video Driver, version 24.0
 /usr/lib/gdm3/gdm-x-session[1966]:         Module class: X.Org Video Driver
 /usr/lib/gdm3/gdm-x-session[1966]:         ABI class: X.Org Video Driver, version 24.0
 /usr/lib/gdm3/gdm-x-session[1966]:         ABI class: X.Org Video Driver, version 24.1
 /usr/lib/gdm3/gdm-x-session[1966]: (II) AMDGPU(0): Set up textured video (glamor)
 /usr/lib/gdm3/gdm-x-session[1966]: (II) Initializing extension XVideo
 /usr/lib/gdm3/gdm-x-session[1966]: (II) Initializing extension XVideo-MotionCompensation
 /usr/lib/gdm3/gdm-x-session[1966]: (II) config/udev: Adding input device Video Bus (/dev/input/event5)
 /usr/lib/gdm3/gdm-x-session[1966]: (**) Video Bus: Applying InputClass "libinput keyboard catchall"
 /usr/lib/gdm3/gdm-x-session[1966]: (II) Using input driver 'libinput' for 'Video Bus'
 /usr/lib/gdm3/gdm-x-session[1966]: (**) Video Bus: always reports core events
 /usr/lib/gdm3/gdm-x-session[1966]: (II) event5  - Video Bus: is tagged by udev as: Keyboard
 /usr/lib/gdm3/gdm-x-session[1966]: (II) event5  - Video Bus: device is a keyboard
 /usr/lib/gdm3/gdm-x-session[1966]: (II) event5  - Video Bus: device removed
 /usr/lib/gdm3/gdm-x-session[1966]: (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:13/LNXVIDEO:01/input/input5/event5"
 /usr/lib/gdm3/gdm-x-session[1966]: (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
 /usr/lib/gdm3/gdm-x-session[1966]: (II) event5  - Video Bus: is tagged by udev as: Keyboard
 /usr/lib/gdm3/gdm-x-session[1966]: (II) event5  - Video Bus: device is a keyboard


--------------------

I also see some audio errors, not sure if these are of a concern.

 sudo journalctl -b | grep -i pulseaudio
 dbus-daemon[816]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service' requested by ':1.37' (uid=121 pid=1068 comm="/usr/bin/pulseaudio --daemonize=no --log-target=jo" label="unconfined")
 systemd[1056]: pulseaudio.service: Succeeded.
 systemd[1056]: pulseaudio.socket: Succeeded.
 pulseaudio[1881]: ALSA woke us up to write new data to the device, but there was actually nothing to write.
 pulseaudio[1881]: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
 pulseaudio[1881]: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.



------------------------------

As for kernel, everything is up to date and will continue to be. 

sudo uname -a
Linux gb-VivoBook-ASUSLaptop-X512DA-F512DA 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


------------------------------

Here is everything in journalctl -b | grep -i error

 kernel: tpm_crb: probe of MSFT0101:00 failed with error -16
 kernel: RAS: Correctable Errors collector initialized.
 kernel: EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
 systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (file watch) being skipped.
 NetworkManager[817]: <warn>  [1588249918.7885] Error: failed to open /run/network/ifstate
 gnome-session-c[1122]: Error creating FIFO: File exists
 gnome-shell[1164]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
 gnome-shell[1454]: Errors from xkbcomp are not fatal to the X server
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 /usr/lib/gdm3/gdm-x-session[1966]:         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
 gnome-session-c[2182]: Error creating FIFO: File exists
 gsd-sharing[2333]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
 gsd-sharing[2333]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
 gnome-shell[2224]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
 gsd-xsettings[1455]: gsd-xsettings: Fatal IO error 11 (Resource temporarily unavailable) on X server :1025.
 tracker-miner-f[1070]: Error while sending AddMatch() message: The connection is closed
 tracker-miner-f[1070]: Error while sending AddMatch() message: The connection is closed
 tracker-miner-f[1070]: Error while sending AddMatch() message: The connection is closed
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 fwupd[2605]: ERROR:esys:src/tss2-esys/esys_context.c:69:Esys_Initialize() Initialize default tcti. ErrorCode (0x000a000a)
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 thunderbird.desktop[3872]: Extension error: Error while loading 'jar:file:///usr/lib/thunderbird/extensions/messagingmenu@mozilla.com.xpi!/manifest.json' (NS_ERROR_FILE_NOT_FOUND) resource
://gre/modules/Extension.jsm:513 :: readJSON/</<@resource://gre/modules/Extension.jsm:513:20
 thunderbird.desktop[3872]: 1588252287846        addons.xpi        WARN        Exception running bootstrap method startup on [EMAIL="messagingmenu@mozilla.com"]messagingmenu@mozilla.com[/EMAIL]: Error: Error while loading 'jar:file:
///usr/lib/thunderbird/extensions/messagingmenu@mozilla.com.xpi!/manifest.json' (NS_ERROR_FILE_NOT_FOUND)(resource://gre/modules/Extension.jsm:513:20) JS Stack trace: readJSON/</<@Extension
.jsm:513:20
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 gnome-shell[2224]: Gio.DBusError: Error calling StartServiceByName for org.freedesktop.FileManager1: Process org.freedesktop.FileManager1 exited with status 1
 gnome-shell[2224]: Error connecting to Nautilus
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
 systemd-resolved[717]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.




thanks, gabo

---

### Post by mörgæs on 2020-05-02
Is the UEFI firmware updated?

---

### Post by gabo4au on 2020-05-05
> **mörgæs said:**
> Is the UEFI firmware updated?


I don't know! I'll have to go figure out how to find out and check it. 

gabo

---

### Post by CelticWarrior on 2020-05-05
Check the drivers/software page of the manufacturer for updates. It's likely you'll find the UEFI updates under what is now erroneously still called "BIOS".

---

### Post by gabo4au on 2020-05-05
Thanks [B]mörgæs and CelticWarrior 
[/B]
That was a good call. I checked the UEFI on my machine, it was at version 306. Checked the ASUS support site and the latest version was 310. I downloaded and updated to that, fingers crossed that it helps!

Another point and question. I just upgraded the RAM, original was 4G on the MB and I installed an 8G chip. Now Ubuntu reports 9.9G? That's very odd to me, here's the line from top.

MiB Mem :   9976.4 total,   6476.9 free,   1748.4 used,   1751.0 buff/cache

That's really a minor issue at this point, 10G is probably ok, 4G wasn't :)


gabo

---

### Post by gabo4au on 2020-05-05
Arrgh.. Just now the screen went blank and it won't come back. I'm not sure if it's locking up the same as before. Before it didn't blank, it just locked. 

Now the screen is going blank and it's locked. I can't even log in via SSH or even get a reply to a ping.

gabo

---

### Post by CelticWarrior on 2020-05-05
The integrated GPU requires some amount of RAM from the main system to be reserved for video. It is often proportional to the total memory available and may or may not be user managed via UEFI settings.
So, the more memory you add the more is reserved for video. Whether or not you can change that value depends on the specific options in UEFI.

---

### Post by gabo4au on 2020-05-05
Thanks. I'm now also seeing these in the kern.log.

 [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring gfx timeout, signaled seq=10580, emitted seq=10582
 kernel: [  485.655256] [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process gnome-shell pid 1865 thread gnome-shel:cs0 pid 1884
 kernel: [  511.530740] [drm:psp_hw_start.cold [amdgpu]] *ERROR* PSP load asd failed!
 kernel: [  511.530805] [drm:psp_resume [amdgpu]] *ERROR* PSP resume failed
 kernel: [  511.530847] [drm:amdgpu_device_fw_loading [amdgpu]] *ERROR* resume of IP block <psp> failed -22


A quick search reveals that these have been associated with lockups from other people in the past. However, the notes I found were from back in 2018 and they were running kernal 4.17 or so. I'm running 5.4.0-29-generic.

But it looks like some sort of problem with the GPU drivers. Unfortunately I can't find any proprietary video drivers. The video is part of the Ryzen 3, here's what it reports in the cpuinfo.

 AMD Ryzen 3 3200U with Radeon Vega Mobile Gfx

gabo


EDIT UPDATE: I checked the AMD site and there are ONLY drivers for win10 for the 3200U.


EDIT_2 Info: Another data point. I had updated to 5.4.0-29-generic last night as that was a new update and I've been updating every day in hopes of finding a solution. However, 5.4.0-29-generic is actually WORSE than 5.4.0.28-generic. With "29" every time the screen blanks, the machine is locked. With "28" at least it runs for a while before it locks. I guess the bright spot is that it seems someone is working on it!

---

### Post by gabo4au on 2020-05-06
Update, I could never get Ubuntu to work correctly with this computer. I don't know if it's the Ryzen 3 3200U that causes the problems (I suspect it is) or if it's some other hardware in the box. 

But this has been the worst Linux experience I've ever had. So I gave up on Ubuntu and went back to win 10, at least it works and doesn't lock up every hour of the day.

gabo

---

### Post by mörgæs on 2020-05-07
You didn't say if you tried a fresh install of 20.04 or only upgrades.
If you want to try Ubuntu again some day then go for the fresh install every time.

---


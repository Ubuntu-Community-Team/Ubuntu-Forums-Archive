---
title: "Boot-up problem"
date: 2012-11-06
forum: General Help
---

### Post by LifeEnemy on 2012-11-06
Hi all,

I'm having trouble with Ubuntu 12.04 on my Acer Aspire One 722. Recently, it started hanging up when booting sometimes. I can get to grub, and then select Ubuntu, and often it will just stop at a blank purple screen instead of continuing. Occasionally the screen will blink, but the purple returns and never seems to finish booting.

Around the same time, it also gives me occasional problems with Wifi. Most days, it stops sending data, though it says it's still connected, and I have to toggle wifi on/off to fix it. Sometimes I have to actually unplug the router and modem to fix it. My roommates are not having these problems, at least not nearly as frequent as I am.

I ask these at the same time because they both started around the time I moved to a new city. I'm not sure if it's related.

Thanks!

---

### Post by LifeEnemy on 2012-11-14
anyone? I seem to be having the same wifi problem in multiple locations, and the only solution it to unplug the modem and router. REALLY annoying, I have to do it multiple times each evening.

help please

---

### Post by varunendra on 2012-11-15
Is the booting problem also still prevalent ? If so, when the system seems to be hung and you have to reboot, post the outputs of these in the very next boot -
```
cat /var/log/dmesg.0 | tail -20
cat /var/log/syslog.1 | tail -20
```

For the wifi issue, when it gives you problems in connecting, follow what is suggested in the following post and post back results : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

---

### Post by LifeEnemy on 2012-11-28
So, I haven't posted because I was waiting for the boot problem to happen again. It seemed to fix itself once I asked. BUT, it just happened, and here's the output:

```

 cat /var/log/dmesg.0 | tail -20
[   20.996252] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.996266] Bluetooth: BNEP filters: protocol multicast
[   21.020114] Bluetooth: RFCOMM TTY layer initialized
[   21.020133] Bluetooth: RFCOMM socket layer initialized
[   21.020139] Bluetooth: RFCOMM ver 1.11
[   21.198017] type=1400 audit(1354143122.078:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=772 comm="apparmor_parser"
[   21.203258] type=1400 audit(1354143122.082:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=772 comm="apparmor_parser"
[   21.327364] init: failsafe main process (736) killed by TERM signal
[   21.332276] [drm] fb mappable at 0x80142000
[   21.332287] [drm] vram apper at 0x80000000
[   21.332293] [drm] size 4325376
[   21.332297] [drm] fb depth is 24
[   21.332302] [drm]    pitch is 5632
[   21.332514] fbcon: radeondrmfb (fb0) is primary device
[   21.332821] Console: switching to colour frame buffer device 170x48
[   21.332914] fb0: radeondrmfb frame buffer device
[   21.332919] drm: registered panic notifier
[   21.332938] [drm] Initialized radeon 2.12.0 20080528 for 0000:00:01.0 on minor 0
[   21.993161] type=1400 audit(1354143122.874:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=850 comm="apparmor_parser"
[   21.994007] type=1400 audit(1354143122.874:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=849 comm="apparmor_parser"
paul@paul-AO722:~$ cat /var/log/syslog.1 | tail -20
Nov 27 15:57:08 paul-AO722 kernel: [ 9708.164340] ICMPv6 NA: someone advertises our address fe80:0000:0000:0000:ee55:f9ff:fe88:afb2 on eth1!
Nov 27 15:59:04 paul-AO722 dhclient: DHCPREQUEST of 140.160.87.205 on eth1 to 1.1.1.1 port 67
Nov 27 15:59:05 paul-AO722 dhclient: DHCPACK of 140.160.87.205 from 1.1.1.1
Nov 27 15:59:05 paul-AO722 dhclient: bound to 140.160.87.205 -- renewal in 394 seconds.
Nov 27 16:03:48 paul-AO722 kernel: [10108.979039] NMI watchdog enabled, takes one hw-pmu counter.
Nov 27 16:03:48 paul-AO722 kernel: [10108.979225] NMI watchdog enabled, takes one hw-pmu counter.
Nov 27 16:03:48 paul-AO722 anacron[5885]: Anacron 2.3 started on 2012-11-27
Nov 27 16:03:48 paul-AO722 anacron[5885]: Will run job `cron.daily' in 5 min.
Nov 27 16:03:48 paul-AO722 anacron[5885]: Jobs will be executed sequentially
Nov 27 16:04:19 paul-AO722 wpa_supplicant[907]: Trying to associate with 68:bd:ab:66:41:21 (SSID='WWUwireless' freq=2412 MHz)
Nov 27 16:04:19 paul-AO722 wpa_supplicant[907]: Association request to the driver failed
Nov 27 16:04:19 paul-AO722 NetworkManager[815]: <info> (eth1): supplicant interface state: completed -> associating
Nov 27 16:04:19 paul-AO722 wpa_supplicant[907]: Associated with 68:bd:ab:85:56:e1
Nov 27 16:04:19 paul-AO722 wpa_supplicant[907]: CTRL-EVENT-CONNECTED - Connection to 68:bd:ab:85:56:e1 completed (reauth) [id=0 id_str=]
Nov 27 16:04:19 paul-AO722 NetworkManager[815]: <info> (eth1): supplicant interface state: associating -> completed
Nov 27 16:05:39 paul-AO722 dhclient: DHCPREQUEST of 140.160.87.205 on eth1 to 1.1.1.1 port 67
Nov 27 16:05:40 paul-AO722 dhclient: DHCPACK of 140.160.87.205 from 1.1.1.1
Nov 27 16:05:40 paul-AO722 dhclient: bound to 140.160.87.205 -- renewal in 410 seconds.
Nov 27 16:08:49 paul-AO722 anacron[5885]: Job `cron.daily' started
Nov 27 16:08:49 paul-AO722 anacron[6007]: Updated timestamp for job `cron.daily' to 2012-11-27

```
I had to suspend my computer twice before I could run these after the boot, so if it looks off that could be why.


Thank you for the help!

---

### Post by wildmanne39 on 2012-11-28
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end. 

Please start a new thread for the wireless issue, only one issue per thread.
Thanks

---

### Post by varunendra on 2012-11-28
I couldn't notice any substantial hints in those outputs. Maybe you can take a look at the dmesg and syslog files yourself (they are in /var/log directory) and post back if anything looks suspicious. The 'dmesg' and 'syslog' files contain messages pertaining to the current session. Same ones with postfixes (e.g. dmesg.0) contain messages from previous sessions. We are interested in any error messages from a previous session when the system hung (for a considerably long period) or crashed.

Meanwhile, please post outputs of -
```
sudo lshw -C display
lsmod
free -m
df -h
```

Also, please edit your post to wrap the outputs in '**Code**' tags like Wild Man asked above. It preserves the output formatting and makes the post look clean, compact and more readable. Here's an example to show you the difference (ignore initial post and read the 'PS:' part only) : [http://ubuntuforums.org/showpost.php?p=12368389&postcount=6](http://ubuntuforums.org/showpost.php?p=12368389&postcount=6)

I also concur with Wild Man about creating a new thread for the wifi issue (in wireless & networking section). Neither this place is correct nor the title is suitable for it.

.

---

### Post by LifeEnemy on 2012-11-30
Apologies about the code tags! They're fixed now. If the wireless issue comes back I'll make a new thread. I didn't want to clutter the forum with threads, but now I know :)

Here are the outputs:

sudo lshw -C display: It showed "PCI (display)" for a little while, then changed to this when I looked again:
```
  *-display               
       description: VGA compatible controller
       product: Wrestler [Radeon HD 6250]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:40 memory:80000000-8fffffff ioport:4000(size=256) memory:90400000-9043ffff

```

lsmod:
```
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
snd_hda_codec_conexant    52554  1 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
snd_hda_codec_hdmi     31775  1 
ppdev                  12849  0 
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211_crypt_tkip    17240  0 
radeon                733789  4 
psmouse                96684  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wl                   2646601  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197599  6 radeon,ttm,drm_kms_helper
lib80211               14040  2 lib80211_crypt_tkip,wl
snd                    62064  20 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                12990  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 radeon
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
mac_hid                13077  0 
wmi                    18744  1 acer_wmi
video                  19068  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
uas                    17828  0 
usb_storage            39646  1 ums_realtek

```

free -m:
```
             total       used       free     shared    buffers     cached
Mem:          1739       1300        438          0         90        444
-/+ buffers/cache:        765        974
Swap:         4767          0       4767

```

df -h:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        17G  5.2G   11G  33% /
udev            863M  4.0K  863M   1% /dev
tmpfs           348M  848K  348M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            870M  440K  870M   1% /run/shm
/dev/sda4       364G  205G  141G  60% /home

```

I'll take a look at the logs when I get a chance, I have a lot of work to do this weekend unfortunately =/

Thanks for all the help!

---

### Post by varunendra on 2012-12-01
Couldn't notice any obvious culprits in the outputs. However, found a [Solved] thread dealing with specifically your model of Acer (Aspire One 722) : ubuntuforums.org/showthread.php?t=1811178

I suggest to read the first post then goto last page and go through the pages in reverse order then, to get an idea about latest updates regarding 12.04 and 12.10.

Basically, here's a few highights I'd suggest to try one at a time, in the given order -
[LIST=1]
[*] Enable "Network Booting" in BIOS *[COLOR="DarkSlateGray"](although I 'believe' that changing the boot order instead so that 'Network booting' goes last in the boot order should be more appropriate, but this is what the thread suggests as the 'fix' to boot problem)[/COLOR]*
[*] Make sure you have linux-headers installed, then try installing the proprietary 'fglrx' driver from "Additional Drivers". To install linux-headers - ```
sudo apt-get install linux-headers-generic
```
[*] Try 12.10 and make sure linux-headers are installed (as above) before trying to install any additional drivers.
[/LIST]

I'm afraid I can't offer any better help than already suggested in that thread, but please let me know if you find any difficulty in understanding or following the suggestions there. Just make sure to try only one thing at a time, and keep note of changes you make.

Let us know what works for you.
Good luck !

---

### Post by LifeEnemy on 2012-12-18
Thanks Varun,

I just had the boot-up problem come back after a few weeks of relative calm (rare problems). It took me many tries before it booted right.

I found that thread when I first bought this comp (had the same freezing problems) and fixed it by putting the net boot first. I put it last and it worked this time, we'll see if it makes any difference or creates more problems. I'll move it back it I have to.

I'm DLing the 12.10 iso now to test it. Maybe it'll fix the performance issues I'm having as well.

Will post back with updates. Thanks!

---

